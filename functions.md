# Functions

Functions are grouped under the following sections

* ### [Initialization section](#initialization)
  * [INIT(CFG)](#initcfg)
  
* ### [Windows objects section](#windows-objects)
  * [MOPTIONS(MESSAGE,TITLE,VALUE,OPTIONS)](#moptionsmessagetitlevalueoptions) 
  * MSGBOX
  * OPTBOX
  * PICKER
  * SPINNER
  
* ### [Windows controls](#windows-controls)

* ### [Windows section](#windows)
* ### [Keys section](#Keys)
* ### [Screen section](#screen)
* ### [Menu section](#menu)
* ### [Scope vars section](#scope-vars)

# Initialization

### INIT(CFG)
>  Initialize the GUI
#### Parameters:
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|CFG      |           | By ref: configuration array. Click [here](./structures.md/#init-configuration) for the description
#### Returns: 
**NOTHING**
___


# Windows objects

### MOPTIONS(MESSAGE,TITLE,VALUE,OPTIONS) 
>  Displays a _modal_ radio button options dialog.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|MESSAGE      |           | String|The message you want to display.
|TITLE      |       Y    | String| The optional title you want to give to the window
|VALUE      |       Y    | String |The name of the selected option. If omitted, nothing will be selected.
|OPTIONS      |     Y      | [RADIO OPTION config](./structures.md/#radio-option-configuration) |The options array.
|WIDTH      |       Y    | Number |If passed, it will override the automatic width computation.
___


### MSGBOX(MESSAGE,TITLE,STYLE,BTNTEXT,TIMED,TTEXT) 
>  Displays a _modal_ Message Box.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|MESSAGE      |           | String / Array| The message you want to display. If an array, dialog will resize the width to accommodate the longest string. If a string, it will split it to accommodate text on multiple rows (max 4) if width is longer than 50 chars.  
|TITLE      |       Y    | String| The optional title you want to give to the window
|STYLE      |       Y    | String |The style of the MessageBox. Allowed values are: "I" for info, "W" for warning and "S" for success. Each style is described in the configuration section. If missing, the default value is "I".
|BTNTEXT      |     Y      | String |If a string is provide, it will be displayed as caption for the button. If omitted, the default text will be used.
|TIMED      |       Y    | Number |If set to a value greater than 0 it represents the number of seconds to display the MSGBOX before it will automatically close. If the value is NEGATIVE, than the countdown is displayed.
|TTEXT      |       Y    | String |If set, it will replace the highlighted section of the countdown text: **Closing** in X seconds...
___

### MSGBOXC(MESSAGE,TITLE,STYLE,BTNTEXT,CHKTEXT) 
>  Displays a _modal_ Message Box with checkbox. It returns the check box status
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|MESSAGE      |           | String / Array| The message you want to display. If an array, dialog will resize the width to accommodate the longest string. If a string, it will split it to accommodate text on multiple rows (max 4) if width is longer than 50 chars.  
|TITLE      |       Y    | String| The optional title you want to give to the window
|STYLE      |       Y    | String |The style of the MessageBox. Allowed values are: "I" for info, "W" for warning and "S" for success. Each style is described in the configuration section. If missing, the default value is "I".
|BTNTEXT      |     Y      | String |If a string is provide, it will be displayed as caption for the button. If omitted, the default text will be used.
|CHKTEXT      |           | String |The text of the check box.
|CHKVALUE      |    Y       | NUmber |The value of the check box. If omitted, checkbox will be **unchecked**.

|Returns | |
|---------  | --------| 
|BOOL       | The check box status

### OPTBOX() 
>  Displays a _modal_ Option Box.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|MESSAGE      |           | String / Array| The message you want to display. If an array, dialog will resize the width to accommodate the longest string. If a string, it will split it to accommodate text on multiple rows (max 4) if width is longer than 50 chars.  
|TITLE      |           | String| The optional title you want to give to the window
|STYLE      |           | String |The style of the MessageBox. Allowed values are: "I" for info, "W" for warning and "S" for success. Each style is described in the configuration section. If missing, the default value is "I".
|BUTTONS      |           | Array |An array of buttons filled with CAPTION and CALLBACK.
|WIDTH      |      Y     | Number |Overrides the automatic width computation

|Returns | |
|---------  | --------| 
|CHAR       | The upper case selected char
___

### OPTBOXC() 
>  Displays a _modal_ Option Box with additional checkbox.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|MESSAGE      |           | String / Array| The message you want to display. If an array, dialog will resize the width to accommodate the longest string. If a string, it will split it to accommodate text on multiple rows (max 4) if width is longer than 50 chars.  
|TITLE      |           | String| The optional title you want to give to the window
|STYLE      |           | String |The style of the MessageBox. Allowed values are: "I" for info, "W" for warning and "S" for success. Each style is described in the configuration section. If missing, the default value is "I".
|BUTTONS      |           | Array |An array of buttons filled with CAPTION and CALLBACK.
|WIDTH      |      Y     | Number |Overrides the automatic width computation
|CHKTEXT      |           | String |The text of the check box.

|Returns | |
|---------  | --------| 
|CHAR^CHECK       | The upper case char of the accelerator of the selected char ^ the check box status.  
___


### WLISTBOX(CFG) 
### LISTBOX(CFG) 
>  Displays a list box. For a single column, add a single [LISTBOX-COLS](./structures.md/#listbox-cols--configuration) to the configuration array.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [LISTBOX](./structures.md/#listbox-configuration) for the description
#### Returns: 
**NOTHING**
___


### WLBSEL(NAME,IX) 
>  Selects an item in the list box. 
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|NAME      |           | String | The name of the List Box to be selected.
|IX      |           | Number | The index in the source array of the entry you want to select.

#### Returns: 
**NOTHING**
___



### WPICKER(TYPE,TITLE,FOREDFLT,BACKDFLT) 
>  Display a modal color picker for both foreground and background, only foreground or only background colors.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|TYPE      |           | String | Use "B" for background, "F" for foreground or "FB" for both.
|TITLE      |        Y   | String | The title of the window.
|DFLT1 | Y | [FORE COLOR / BACK COLOR](./constants.md/#colors) | The default color to be selected if only one color is requested, foreground color if noth fore and bgnd are requested.. If omitted, the first color will be auto selected. 
|DFLT2 | Y | [BACK COLOR](./constants.md/#background-colors) | The default background color to be selected. If omitted, the first color will be auto selected. 

####  Returns:
**COLORS** foreground color^background color.
___

### MSPINNER(MESSAGE,TITLE,VALUE,MIN,MAX) 
>  Display a modal numeric spinner.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|MESSAGE      |           | String | The message to be displayed above the spinner.
|TITLE      |           | String | The title of the window.
|VALUE      |           | Number | The starting value of the spinner.
|MIN      |           | Number | The minimum value 
|MAX      |           | Number | The maximum value 

####  Returns:
**NUMBER** The selected number or the original value (if window was Canceled)
___

### WTREE2L(CFG) 
>  Displays a 2 level tree.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [TREE2L](./structures.md/#tree2l-configuration) for the description
#### Returns: 
**NOTHING**
___



### WINPUT(MESSAGE,TITLE,MAXL,DFLTTXT,GROUP) 
>  Displays a text box.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|MESSAGE      |           | String | The caption for the text box. The maximum length is 70. If longer, text will be clipped.
|TITLE      |    Y       | String | The title of the window.
|MAXL      |           | Number | The maximum length of the returned string. The value must be between 1 and 70.
|DFLTTXT      |           | String | The initial value of the text. If longer than the MAXL it will be truncated.
|GROUP      |           | String/Array | The group you want to restrict input to. If one only, use a string, or use an array for multiples. Select one (or more) of the following values:
|           |           |  | "NUMBER"
|           |           |  | "LCHAR"
|           |           |  | "UCHAR"
#### Returns: 
**NOTHING**
___

### WCHKBOX(CFG) 
### CHKBOX(CFG) 
>  Displays a check box
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [CHECKBOX](./structures.md/#checkbox-configuration) for the description
#### Returns: 
**NOTHING**
___


### WOPTION(CFG) 
### RADIO(CFG) 
>  Displays a radio button group
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [RADIO config](./structures.md/#radio-configuration) for the description
#### Returns: 
**NOTHING**
___


### FRAME(CFG) 
>  Displays a radio button group
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [FRAME config](./structures.md/#frame-configuration) for the description
#### Returns: 
**NOTHING**
___

### FRMWRITE(NAME,TEXT) 
>  Writes text into the frame.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|NAME      |           | String | The name of the frame
|TEXT      |           | String | The text you want to display. It will be automcally splitted in multiple rows.

#### Returns: 
**NOTHING**
___


### TABBER(VERB)
>  Enable tabbing (using the TAB key) between multiple text boxes. It ASSUMES that each text box in the window has the "TAB" set. IMPORTANT: This function MUST be called AFTER all the text boxes are created.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|VERB      |      Y     | String | The action: currently supported only UPDATE

#### Returns: 
**NOTHING**
___

### SCROLLER(CFG) 
>  Displays a scroller
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [SCROLLER config](./structures.md/#frame-configuration) for the description
#### Returns: 
**NOTHING**
___

### LABEL(CFG) 
>  Displays a label
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:|   :---: | ----------|
|CFG      |           | [LABEL config](./structures.md/#label-configuration) for the description
#### Returns: 
**NOTHING**
___

# Windows

### WOPEN(CFG) 
>  Creates a Window
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|CFG      |           | [WOPEN](./structures.md/#wopen-configuration) | A structure defining the window.
#### Returns: 
**HWIN**
> This function can be called also as DO and ignore the return value.
___
### WCLOSE 
>  Closes the current window
#### Returns: 
**NOTHING**
___

### WHIDE 
>  Hides the current window and return the focus to its parent
#### Parameters:
**NOTHING**
#### Returns: 
**NOTHING**
___

### WINSEL(HWIN) 
>  Selects a window
#### Parameters:
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|HWIN      |Y           | A valid Window handle
#### Returns: 
**NOTHING**
___

### WREFRESH 
>  Refresh the current 
#### Returns: 
**NOTHING**
___


### WINMOVE 
>  Moves the current window
#### Returns: 
**NOTHING**
___

### WINCLEAR(BGND) 
>  Clears the current (or selected, if HWIN is passed) client area of the window

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|BGND |Y           | The background color. If omitted, it will use the default color.

#### Returns: 
**NOTHING**
___

### WSETPOS(X,Y) 
>  Position the cursor within a window

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|X          |           | The current column (1 to 80) within the current windows (or the window pointer by HWIN
|Y          |           | The current row (1 to 24) within the current windows (or the window pointer by HWIN

#### Returns: 
**NOTHING**
> NOTE: The X and Y coordinates are CLIENT AREA 1,1 based. So, 1,1 refers to the upper left of the current window, within the border
___

### WGETNODE(NODE) 
>  Returns the current HWIN information 

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|NODE          |           | An array to hold the returned information

#### Returns: 
**NOTHING**
___

### WWRITE(STR,X,Y) 
>  Writes text in a window. Optionally, text can be centered, pushed right or left.
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|STR      |           | String|The message you want to display.
|X |           | String / Number| if numeric, than it is the relative X position. If string, it can be "L" for left, "R" for right and "C" for center.
|Y     |           | Number|The relative Y position.
___

### SREFRESH 
>  Refresh the entire screen, up to the top-most window
#### Parameters:
**NOTHING**
___


# Keys

### WKEYAARY(KEYS) 
>  Adds a key array to the key queue

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 KEYS          | | An array with the character as subscript and the callback as value.
 CALLBACK      | | A string with the routine to be executed. It may include embedded parameters
 EXIT |Y |  1 if we want to exit. An eventual callback will be executed before to exit

#### Returns: 
**NOTHING**


### WKEYADD(CHAR,CALLBACK,EXIT) 
>  Adds a key to the key queue

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 CHAR          | | Character in the format:CHAR^MOD where MOD is a string containing ASC for Alt, Control and Shift
 CALLBACK      | | A string with the routine to be executed. It may include embedded parameters
 EXIT |Y |  1 if we want to exit. An eventual callback will be executed before to exit

#### Returns: 
**NOTHING**
> NOTE: The X and Y coordinates are CLIENT AREA 1,1 based. So, 1,1 refers to the upper left of the current window, within the border
___


### WKEYADDX(CHAR,CALLBACK,EXIT) 
>  Adds both lower and upper case version of a key to the key queue

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 CHAR          | | Character in the format:CHAR^MOD where MOD is a string containing ASC for Alt, Control and Shift
 CALLBACK      | | A string with the routine to be executed. It may include embedded parameters
 EXIT |Y |  1 if we want to exit. An eventual callback will be executed before to exit

#### Returns: 
**NOTHING**
> NOTE: The X and Y coordinates are CLIENT AREA 1,1 based. So, 1,1 refers to the upper left of the current window, within the border
___


### WKEYADDA(GROUP,CALLBACK) 
>  Adds an ASCII character set, like ALPHA, NUM, etc.

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 GROUP          | | Any of the following strings
 | | | ALPHA  All alphanumeric characters
 | | | UALPHA  All upper case alphanumeric characters
 | | | LALPHA  All lower case alphanumeric characters
 | | | NUM     All numbers
 | | | SYMBOLS All symbols
 CALLBACK          | | The callback with optional (RET) parameter
 

#### Returns: 
**NOTHING**
___


### WKEYRMV(CHAR) 
>  Removes a key from the key queue

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 CHAR          | | Character in the format:CHAR^MOD where MOD is a string containing ASC for Alt, Control and Shift

#### Returns: 
**NOTHING**
> NOTE: The X and Y coordinates are CLIENT AREA 1,1 based. So, 1,1 refers to the upper left of the current window, within the border
___


### WKEYRMVX(CHAR) 
>  Removes both lower and upper case version of a key from the key queue

#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
 CHAR          | | Character in the format:CHAR^MOD where MOD is a string containing ASC for Alt, Control and Shift

#### Returns: 
**NOTHING**
___


### WKEYCLEAR 
>  Clears the key queue
#### Returns: 
**NOTHING**
___

### GETANYK(ECHO) 
>  Returns when ANY key is pressed


#### Parameters:
  
|Parameter  | Optional  | Description |
|---------  | :--------:|   ----------|
|ECHO       |Y          | If set will not switch echo off and on again. This improves speed in keyboard loops (p.e. scrolling)|

#### Returns: 
**NOTHING**
 
___

# Screen

### SBWRITE(STR,ZONE,NOBUFF) 
>  Writes in the status bar or in a specific status bar zone
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|STR      |           | String|The message you want to display.
|ZONE |    Y       | Number| The zone number. If omitted, it will be a no-zone statusbar or fill the first zone.
|NOBUFF |    Y       | Number| 1 if you don't want to use the circular buffer. 
___

### SBRESTR(STR,ZONE) 
>  Restores the status bar or the a specific status bar zone
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|ZONE |    Y       | Number| The zone number. If omitted, it will either restore a no-zone statusbar or restore the first zone.
___

### SBGET(ZONE,BUFF) 
>  Gets the current status bar text (on each zone) or the buffer text
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|ZONE |    Y       | Number| The zone number. If omitted, it will either restore a no-zone statusbar or restore the first zone.
|BUFF| Y | Number | If set to 1, it will return the text in the buffer
___

### SETTITLE(TEXT) 
>  Changes the title of the main screen
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
|TEXT |           | String| The new text.
___

### GETTITLE(TEXT) 
>  Returns the title of the main screen
#### Parameters:
**NOTHING**
#### Returns:
The current title
___


# Menu

### MNUSET(NAME,KEY,VALUE)
>  Changes menu attributes and regenerates the menu
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 NAME         | | String | The name of the menu you want to edit
 KEY       | | String | A string out of the following values:
 |  |   |  | CAPTION
  | | |  | DISABLED
 | | |  | CHECKED
 | | |  | HELP
 | | |  | EXIT
 | | |  | ACCELL
 VALUE     | | String |The value you want to set
___

### MNUSETA(ARY)
>  Changes menu attributes and regenerates the menu of many items in one go
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 ARY         | | Array | An array with the same entries as MNUSET ARY(NAME,KEY)=VALUE
___

### MNUGET(NAME,KEY)
>  Changes menu attributes and regenerates the menu
#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 NAME         | | String | The name of the menu you want to edit
 KEY       | | String | A string out of the following values:
 |  |   |  | CAPTION
  | | |  | DISABLED
 | | |  | CHECKED
 | | |  | HELP
 | | |  | EXIT
 | | |  | ACCELL
___

# Scope vars

### GETVARNM(SYSTEM) 
>  Returns the name of the scope variable

#### Parameters:
**NOTHING**
  
#### Returns: 
**NOTHING**
___

### GETVAR(RETVAL,LEG1,LEG2,LEG3,LEG4,LEG5) 
>  Returns the value (or tree) of a specific scope variable (in the current HWIN)

#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 RETVAR         | | Array | The array (passed by reference) that will be populated with the requested variable.
 LEG1         | | String | The variable name you wish to get
 LEG2         | Y | String | The variable name you wish to get
 LEG3         | Y | String | The variable name you wish to get
 LEG4         | Y | String | The variable name you wish to get
 LEG5         | Y | String | The variable name you wish to get
  
#### Returns: 
**NOTHING**
___

### SETVAR(VALUE,LEG1,LEG2,LEG3,LEG4,LEG5) 
>  Sets the value of a specific scope variable (in the current HWIN)

#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 VALUE         | | String / Array | The string / array (passed by reference) that will populate the requested variable.
 LEG1         | | String | The variable name you wish to get
 LEG2         | Y | String | The variable name you wish to get
 LEG3         | Y | String | The variable name you wish to get
 LEG4         | Y | String | The variable name you wish to get
 LEG5         | Y | String | The variable name you wish to get
  
#### Returns: 
**NOTHING**
___

### KILLVAR(LEG1,LEG2,LEG3,LEG4,LEG5) 
>  Kills the node of a specific scope variable (in the current HWIN)

#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 LEG1         | | String | The variable name you wish to get
 LEG2         | Y | String | The variable name you wish to get
 LEG3         | Y | String | The variable name you wish to get
 LEG4         | Y | String | The variable name you wish to get
 LEG5         | Y | String | The variable name you wish to get
  
#### Returns: 
**NOTHING**
___


### GETVARS(HWIN,ARRAY) 
>  Returns the name of the scope variable

#### Parameters:
|Parameter  | Optional  | Data type | Description |
|---------  | :--------:| :----: |  ----------|
 HWIN         | | Number | A valid HWIN
 ARRAY         | | Array | The array (passed by reference) that will be populated with the variables structure.
  
#### Returns: 
**NOTHING**
___

