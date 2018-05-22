# Sublime Test 3 Customizations for Datamine Studio RM Macros

These customizations add a colour scheme, snippets, and commenting support to Sublime Text 3 for Datamine macros.

## Installation

Use `Package Control` to install the latest version:

1. Press Ctrl + ⇧ + P to open the command palette.
2. Type `Package Control: Install Package` and press enter. Then search for `DM Macro`.

Once installed open a Datamine macro file with the '.mac' extension. Go to the `View->Syntax->Open all with current extension as...` menu and select `dm-macro`.

## Syntax definition

The macro language syntax highlighting definition allows special highlighting of process names and there parameters, variables, and comments in Datamine macros. This scheme defines sub-schemes for language elements of EXTRA, LET, PICREC, and the DOS batch language. Certain errors such as incorrect variable, keyword, and file names are highlighted to help reduce bugs in macro code.

I have tested this scheme with the Material Colour Scheme, other colour schemes may not work as well.

## Snippets

Snippets are small pieces of code, mainly for Datamine macro processes. When you type the first letters of a Datamine keyword a prompt will appear at the cursor where you can select the snippet. Snippets are included for many processes with common options and defaults. These snippets are not exhaustive -- I will add additional snippets to the repository as I need them.

### Compatibility

The snippets have only been tested in Sublime Text 3 (they should work in version 2 and also in TextMate). The snippets were originally designed to work with Datamine Studio 3 but are in the process of being transferred to Studio RM. As such there may be commands or command options that will not work in Studio 3.

### Coding conventions

* All snippets are in lowercase except where certain Datamine field names are used. Field names are in uppercase as per Datamine conventions (e.g., BHID, FROM, TO, XMORIG, XINC).
* Because of the 80-character line length limit of Datamine macros the use of spaces (white space) in the snippets is minimized. No spaces are used if not strictly necessary for the code to be valid. The exception to this is a two-space indent for the second and subsequent lines of Datamine processes.
* By default snippets contain the full set of parameters even when this makes no sense -- it is up to the user to modify the code according to its application. Some verbose commands may have one or more alternative forms for specific application (e.g. the ESTIMA command is presented in a simpler form without the unfolding parameters). Other forms are also present for specific common tasks such as a SELCOP command for copying a drillhole file with the required drillhole fields included:

```
!selcop &in(),&out(),
  *f1(BHID),*f2(FROM),*f3(TO),*f4(LENGTH),
  *f5(X),*f6(Y),*f7(Z),*f8(A0),
  *f9(B0),*f10(),*f11(),*f12(),
  *f13(),*f14(),*f15(),*f16(),
  @keepall=0
```

* Snippet place-holder variables are used for all parameters. Where a parameter has a default value in Datamine this default is present in in the place-holder. Sometimes the Datamine default is overridden if another default is more common (e.g., the Datamine default for COMPDH's MODE parameter is 0 but the snippet is defaulted to 1). The override of default values is purely based on my personal preference.
* Some documentation of parameters is provided as a Datamine comment below the command. This is slowly being implemented for the more complicated commands:

```
!mgsort &in(),&out(),
  *key1(),*key2(),*key3(),*key4(),
  @order=1,@keyfrst=1,@roworder=1

# &in input file; &out sorted output file; *key1*...n any number of key
# fields for sorting; @order sort order (1: ascending; 2: decending);
# @keyfrst (0: output field in same order as input; 1: key fields first);
# @roworder (0: rows with identical keyfield in any order -- faster;
# 1: rows in input file order -- slowest).
```

## Commenting support

With commenting support when you select lines in a macro and type Ctrl + / the lines will be commented with '#'. If the lines are already commented they will be un-commented.