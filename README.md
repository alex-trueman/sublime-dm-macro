# Sublime Test 3 Customizations for Datamine Studio RM Macros

These customizations add a colour scheme, snippets, and commenting support to Sublime Text 3 for Datamine macros.

## Installation

Use `Package Control` to install the latest version:

1. Press Ctrl + ⇧ + P to open the command palette.
2. Type `Package Control: Install Package` and press enter. Then search for `DM Macro`.

Once installed open a Datamine macro file with the '.mac' extension. Go to the `View->Syntax->Open all with current extension as...` menu and select `dm-macro`.

## Syntax definition

The syntax definition defines the structure Datamine macros. This is used for syntax highlighting of elements such as comments, key words, strings, variables, and errors. This scheme defines sub-schemes for language elements of EXTRA, LET, PICREC, and the DOS batch language. Certain errors such as incorrect variable, keyword, and file names are highlighted to help reduce bugs in macro code.

I have used this scheme with the Material Colour Scheme, other colour schemes may not work as well.

## Snippets

Snippets are small pieces of code, mainly for Datamine macro processes. When you type the first letters of a Datamine keyword a prompt will appear at the cursor where you can select the snippet. Snippets are included for many processes with common options and defaults.

## Commenting support

With commenting support when you select lines in a macro and type Ctrl + / the lines will be commented with '#'. If the lines are already commented they will be un-commented.