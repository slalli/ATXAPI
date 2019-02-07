# Structures

#### [INIT config](#init-configuration) 
#### [WOPEN config](#wopen-configuration)
#### [WBUTTON config](#wbutton-configuration)
#### [MENU config](#menu-configuration)
#### [KEYS config](#keys-configuration)
#### [ZONE config](#zone-configuration)
#### [LISTBOX config](#listbox-configuration)
#### [LISTBOX-COLS config](#listbox-cols-configuration)
#### [TREE2L config](#tree2l-configuration)
#### [TEXTBOX config](#textbox-configuration)
#### [CHECKBOX config](#checkbox-configuration)
#### [RADIO config](#radio-configuration)
#### [RADIO OPTION config](#radio-option-configuration)
#### [FRAME config](#frame-configuration)
#### [SCROLLER config](#scroller-configuration)
#### [LABEL config](#label-configuration)
___

## INIT  configuration
   
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
  `CFG("COLOR")`| Y | [FORE COLOR](./constants.md/#foreground-colors) | The foreground color of the window. 
  `CFG("BGND")`|  Y | [BACK COLOR](./constants.md/#background-colors) | The background color of the window.
  `CFG("TITLEBAR","COLOR")`|  Y | [FORE COLOR](./constants.md/#foreground-colors) | The foreground color of the title bar
  `CFG("TITLEBAR","BGND")`|  Y | [BACK COLOR](./constants.md/#background-colors) |  The background color of the title bar
  `CFG("TITLEBAR","FILL")`| Y | String | The fill mode of the title bar. "B" for boxed or "L" for line.
  `CFG("TITLEBAR","TITLE","TEXT")`| Y | String | The title of the window. If missing, the title bar will not be displayed.
  `CFG("TITLEBAR","TITLE","ALIGN")`| Y | String | The alignment mode of the title text. "L" for left, "R" for right or "C" for center.
  `CFG("STATUSBAR","BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the zone. If omitted, the parent STATUSBAR background color will be used.   
  `CFG("STATUSBAR","FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the zone. If omitted, the parent STATUSBAR foreground color will be used.  
  `CFG("STATUSBAR","TEXT")`|     Y      | String  | The default text to be filled at SCREEN creation. If omitted, the separator line won't be displayed.  
  `CFG("STATUSBAR","SEPLINE")`| Y | [COLOR](./constants.md/#colors) | The color of the separator lines. 
  `CFG("STATUSBAR","ZONES",n)` | Y | [ZONE](#zone-configuration) array | Eventual multiple status zones, each with independent control.
  `CFG("CURSOR","SHOW")` | Y | Number | 1 if show cursor when leaving menus and status display. If omitted, it will use the default settings.
  `CFG("VARNAME")` | Y | string | The name of the variable to be used for window-scope. If omitted, the default value will be used.
  `CFG("MENU","ROOT","BGND")`|  Y | [COLOR](./constants.md/#colors) | The background color of the menu bar.
  `CFG("MENU","ROOT","FORE")`|  Y | [COLOR](./constants.md/#colors) | The foreground color of the menu bar.
  `CFG("MENU","ROOT","SELBGND")`|  Y | [COLOR](./constants.md/#colors) | The selected background color of the menu bar.
  `CFG("MENU","ROOT","SELFORE")`|  Y | [COLOR](./constants.md/#colors) | The selected foreground color of the menu bar.
  `CFG("MENU","ROOT","DISFORE")`|  Y | [COLOR](./constants.md/#colors) | The disabled foreground color of the menu bar.
  `CFG("MENU","ROOT","ACC")`|  Y | [COLOR](./constants.md/#colors) | The accelerator color of the menu bar.
  `CFG("MENU","ROOT","SELACC")`|  Y | [COLOR](./constants.md/#colors) | The selected accelerator color of the menu bar.
  `CFG("MENU","WINS","BGND")`|  Y | [COLOR](./constants.md/#colors) | The background color of the menu window.
  `CFG("MENU","WINS","SELBGND")`|  Y | [COLOR](./constants.md/#colors) | The selected background color of the menu window.
  `CFG("MENU","WINS","FORE")`|  Y | [COLOR](./constants.md/#colors) | The foreground color of the menu window.
  `CFG("MENU","WINS","ACC")`|  Y | [COLOR](./constants.md/#colors) | The accelerator color of the menu window.
  `CFG("MENU","WINS","DISFORE")`|  Y | [COLOR](./constants.md/#colors) | The disabled foreground color of the menu window.
  `CFG("MENU","WINS","BLINE")`| Y |[COLOR](./constants.md/#colors) | The border color of the menu window.
  `CFG("MENU","WINS","OFFSET")`| Y | Number | The padding at the left and at the right of the menu entry in the menu window. 
  `CFG("MENU","WINS","CHECKCHAR")`| Y | Number | The ASCII character to be used to highlight a checked item in the menu 
  `CFG("MENU","WINS","CHECKBGND")`| Y | Number | The background color to be used to highlight a checked item in the menu 
  `CFG("MENU","WINS","CHECKFORE")`| Y | Number | The foreground color to be used to highlight a checked item in the menu 
  `CFG("MENU","TREE")`| Y | [MENU](#menu-configuration) | The menu structure. If missing, no menu will be displayed. 
  `CFG("EVENTS","ONAPPSTART")`| Y | String | This optional callback will be executed when the application is starting. Here you can display a welcome screen and execute your app initialization. This code will be executed **AFTER** the main screen is created, so you can write to the screen right away. (the current HWIN is set to SCREEN) 
  `CFG("EVENTS","ONAPPEND")`| Y | String | This optional callback will be executed **AFTER** the EXIT procedure is completed, right before to exit the INIT call. Here you can perform garbage collection.  
  `CFG("SCREEN","WIDTH")`| Y | Number | This entry determine the width of the screen. It can be either 80 or 132. If omitted, the default value will be used. If a value different than 80 or 132 is used, than the INIT will return and the GUI won't start.  
  `CFG("SCREEN","EVENTS","ONLOAD")`| Y | String | The entry point of the code to be executed right after the window is created. If omitted, no code will be executed.  
  `CFG("SCREEN","EVENTS","ONUNLOAD")`| Y | String | The entry point of the code to be executed right after the window is closed. If omitted, no code will be executed.  
  `CFG("SCREEN","EVENTS","REFRESH")`| Y | String | The entry point of the code to be executed when a screen refresh is needed. If omitted, no code will be executed and the refresh will have to occur manually. However, the window will be repainted automatically, only the client area will be ignored..
  `CFG("HELP","KEY"`| Y | [KEYS](./constants.md/#keys) / Number | The key that will be used to pop up the Context Sensitive Help. If omitted, the default value will be used. Set to -1 to REMOVE Context Sensitive Help.
  `CFG("HELP","H"`| Y | Number | The height of the help window. If omitted, the default value will be used.
  `CFG("HELP","W"`| Y | Number | The Width of the help window. If omitted, the default value will be used.
  `CFG("SCREEN",HELPKEY"`| Y | String | The help KEY to be used for the main screen.
___


## WOPEN configuration 

|Node |Optional  |Data type |   Description 
|---------  | :---: | :---:|   ----------|
|`CFG("POS","X")`| Y          |Number | The horizontal coordinate, 1 based. The valid range is 1 to 80.  
|`CFG("POS","Y")`| Y          |Number | The vertical coordinate, 1 based. The valid range is 1 to 24.  
|`CFG("SIZE","H")`|           |Number | The height of the window, 1 based. The valid range is 1 to 24. If not present, the window will be horizontally centered.
|`CFG("SIZE","W")`|           |Number | The width of the window, 1 based. The valid range is 1 to 80. If not present, the window will be vertically centered.
|`CFG("COLORS","BGND")`|  Y         |[COLOR](./constants.md/#colors) | The background color. If not present, the default value will be used.  
|`CFG("COLORS","FORE")`|  Y         |[COLOR](./constants.md/#colors) | The foreground color. This color will be set on the ATX("FORE") constant. If not present, the default value will be used.  
|`CFG("COLORS","BORDER")`|  Y         |[COLOR](./constants.md/#colors) | The border color. If not present, the default value will be used.  
|`CFG("COLORS","SHADOW")`|  Y         |[COLOR](./constants.md/#colors) | The shadow color. If not present, the default value will be used. If -1, no shadow will be drawn
|`CFG("TITLEBAR","TITLE")`|  Y         |String | An eventual title for the window. If present, it will be displayed centered on the top of the window and in the border color.
|`CFG("TITLEBAR","LINE")`|  Y         |String | It can be: "L" for line, "B" for block or _empty_ for default value.
|`CFG("EVENTS","ONLOAD")`|  Y         |String | The entry point of the code to be executed right after the window is created. If omitted, no code will be executed.
|`CFG("EVENTS","ONUNLOAD")`|  Y         |String | The entry point of the code to be executed right after the window is closed. If omitted, no code will be executed.
|`CFG("EVENTS","REDRAW")`|  Y         |String | The entry point of the code to be executed when a screen refresh is needed. If omitted, no code will be executed and the refresh will have to occur manually. However, the window will be repainted automatically, only the client area will be ignored..
|`CFG("AUTOCLOSE")`|  Y         |Number | 1 if the ESCAPE key will close the window. 0 if no automatic handler is wanted, _empty_ if the default value have to be used.
|`CFG("KEYS")`|  Y         |[KEYS](./constants.md/#keys) | An array of KEYS and related handlers to be added to the window.
|`CFG("BELL")`|  Y         |Number | 1 if you want to sound the bell
|`CFG("STATUSBAR")`|  Y         |String | The text you want to, optionally, display on the Status Bar. The previous text will be automatically restored when the window closes.
|`CFG("HELPKEY")`|  Y         |String | The optional Help KEY used to fetch the Context Sensitive Help.
___

## WBUTTON configuration

|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|**ONE BUTTON ONLY**|           || **Use the following entries to add a single button.**  
|`CFG("POS","X")`|           |Number / String | The horizontal coordinate, 1 based. The valid range is 1 to 80. It is possible to align the button by using "L" for left, "R" for right and "C" for center.  
|`CFG("POS","Y")`|           |Number / String | The vertical coordinate, 1 based. The valid range is 1 to 24. It is possible to align the button by using "T" for top, "B" for bottom and "C" for center.  
|`CFG("CAPTION")`|           |String| The text to be displayed. An accelerator key can be set by prefixing the character by the & symbol.     
|`CFG("DISABLED")`| Y          |Number| 1 if disabled, 0 or _empty_ if enabled. Default is enabled   
|`CFG("EXIT")`| Y          |Number| 1 if you want to exit the application   
|`CFG("KEYNOALT")`| Y          |Number| 1 if you want to trap also the accelerator key with no ALT modifier.   
|`CFG("COLORS","BGND")`|  Y         |[COLOR](./constants.md/#colors) | The background color. If not present, the default value will be used.  
|`CFG("COLORS","FORE")`|  Y         |[COLOR](./constants.md/#colors) | The foreground color. This color will be set on the ATX("FORE") constant. If not present, the default value will be used.  
|`CFG("COLORS","DISBGND")`|  Y         |[COLOR](./constants.md/#colors) | The disabled background color. If not present, the default value will be used.  
|`CFG("COLORS","DISFORE")`|  Y         |[COLOR](./constants.md/#colors) | The disabled foreground color. This color will be set on the ATX("FORE") constant. If not present, the default value will be used.  
|`CFG("COLORS","ACC")`|  Y         |[COLOR](./constants.md/#colors) | The accelerator color. This color will be set on the ATX("FORE") constant. If not present, the default value will be used.  
|`CFG("COLORS","BORDER")`|  Y         |[COLOR](./constants.md/#colors) | The border color. If not present, the default value will be used.  
|`CFG("HOFFSET")`|  Y         |Number | The number of space characters to add at the left and right of the string. This value can be 0 to remove any traling / leading characters. If missing, the default value will be used.  
|`CFG("CALLBACK")`|      Y     |String | The entry point of the code to be executed when the button is pressed (the accelerator key is pressed). Note: if an accelerator is present, than a CALLBACK must be also present of the button will not draw to prevent crashes,  
|`CFG("ENTERSEL")`|      Y     |Number | If set to 1, the enter key will trigger the callback as well...  
|**MULTIPLE BUTTONS**|           || **Use the following entries to add a button group.**|  
|`CFG(number>0)`|           |Number | You can add multiple buttons at the same time and group / align them anywhere in the window. The structure is the same as for the single button, with the exception of the "POS" node, which does NOT need to be filled in. 
|`CFG("ALIGN","H")`|           |String| Select how to horizontally align the button. Valid values are: "L" for left, "R" for right, "C" for center. This value don't need to be set when "ORDER" is set to "H". 
|`CFG("ALIGN","V")`|           |String  / Number| Select how to vertically align the button. Valid values are: "T" for top, "B" for bottom, "C" for center. If it is a numeric value, it represents the Y value. 
|`CFG("ORDER")`|           |String|  If "H", than all the buttons are horizontally spread, if "V" buttons are tied together, spaced by 1 row.
|`CFG("HOFFSET")`|  Y         |Number | The number of space characters to add at the left and right of the string. If this value is missing, the default value will be used. This value can be 0 to remove any traling / leading characters. If missing, the default value will be used. This will apply to ALL buttons and will override eventual individual settings in the multiple WBUTTON structures.  
|`CFG("VOFFSET")`|  Y         |Number | The number of space characters to add between the buttons when ORDER="V". If this value is missing, the default value will be used. This value can be 0 to remove any traling / leading characters. If missing, the default value will be used.   
|`-------`|  -------         |------ | -------------------------------------------------   
|`CFG("SEPARATOR")`|  Y         |Number | If set, instead of a button a 1 line separator will be displayed. This allows to create button GROUPS and still align them. At the present, working only on V align.    
|`CFG`|    Y       | String | If set to "REFRESH" it will refresh the list box having the name equals to  CFG("NAME")
___

## MENU configuration

|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|**ONE BUTTON ONLY**|           || **Use the following entries to add a single button.**  
|`CFG("POS","X")`|           |Number / String | The horizontal coordinate, 1 based. The valid range is 1 to 80. It is possible to align the button by using "L" for left, "R" for right and "C" for center.  
___

## KEYS configuration

> The KEYS structure is used to pass "keys" information used in triggering events.
  It is an array of multiple keys information, describing the key (a keyboard character or command, like F1, PAGE DOWN, etc. ), its modifiers (control, alt and shift) and the related  callback (routine to be executed when key is pressed).

|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|**ONE BUTTON ONLY**|           || **Use the following entries to add a single button.**  
|`CFG("POS","X")`|           |Number / String | The horizontal coordinate, 1 based. The valid range is 1 to 80. It is possible to align the button by using "L" for left, "R" for right and "C" for center.  
___

## ZONE configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`ZONE("WIDTH")`|           | Number  | The width of the zone. Use "*" for an elastic zone (auto-stretch). Note: you can have only ONE elastic zone. Entries BEFORE the * are aligned left, entries AFTER the * are aligned right.  
|`ZONE("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the zone. If omitted, the parent STATUSBAR background color will be used.   
|`ZONE("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the zone. If omitted, the parent STATUSBAR foreground color will be used.  
|`ZONE("TEXT")`|     Y      | String  | The default text to be filled at SCREEN creation.  
___

## LISTBOX configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The name of the listbox object, for further reference.
|`CFG("ARRAY"`|           | String | The $NAME of the array / global you want to use as data source
|`CFG("HEIGHT"`|           | Number | 
|`CFG("X"`|           | Number | 
|`CFG("Y"`|           | Number | 
|`CFG("MULTISEL"`|    Y       | Number | 1 if the list box uses multi-select mode 
|`CFG("MSELSPACE"`|    Y       | Number | If set, ENTER will multi-select and not SPACE  
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the listbox. If omitted, the default value will be used.   
|`CFG("BORDER")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The border color of the listbox. If omitted, the default value will be used.  
|`CFG("HEADER")`|     Y      | Number  | Set this value to 1 if you want to display the title bar.  
|`CFG("HEADER","BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)   | The background color of the title bar. If omitted, the default value will be used.  
|`CFG("HEADER","FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the title bar. If omitted, the default value will be used.
|`CFG("HEADER","SEPA")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the separator between the header and the data. If omitted, the default value will be used.
|`CFG("ITEM","BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the item. If omitted, the default value will be used.  
|`CFG("ITEM","FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)   | The foreground color of the item. If omitted, the default value will be used.
|`CFG("ITEM","SELBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)   | The background color of the selected item. If omitted, the default value will be used.  
|`CFG("ITEM","SELFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the selected item. If omitted, the default value will be used.
|`CFG("ITEM","MSELBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)   | The background color of the selected item when in multi-select mode. If omitted, the default value will be used.  
|`CFG("ITEM","MSELFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the selected item when in multi-select mode. If omitted, the default value will be used.
|`CFG("ITEM","COLSSEP")`|     Y      | String  | The character to be used to separate the columns. If omitted, the default value will be used.
|`CFG("ITEM","COLORSUBSCRIPT")`|     Y      | String  | The eventual subscript that contains the Foreground color of the specific row. If omitted, the default color will be used.
|`CFG("ITEM","COLS",n)`|           |  [LISTBOX-COLS](#listbox-cols-configuration) | An array with the description of the columns. A one-column listbox will have a single entry.
|`CFG("KEYSUSELR")`|      Y     |  Number | If set, CURSOR LEFT and CURSOR RIGHT will be used to scroll, instead of CURSOR UP and CURSOR DOWN.
|`CFG("EVENTS","ONSELECT")`|     Y      | String  | The callback to be executed when an entry is selected. It returns the index in the passed parameters X.
|`CFG("SELCOL"`|    Y       | Number | If set to 1, the row selection will highlight only the first column.
|`CFG`|    Y       | String | If set to "REFRESH" it will refresh the list box having the name equals to  CFG("NAME")
  
___

## LISTBOX-COLS configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`COLS("WIDTH")`|           | String | The width of the column.
|`COLS("SUBSCRIPT")`|   This OR/AND next        | String | The subscript to bind the column to.
|`COLS("PIECE")`|    This OR/AND previous       | Number | The piece to bind the column to.
|`COLS("TITLE")`|    Y       | String | The title of the column that will appear in the title bar.
|`COLS("ALIGN")`|    Y       | String | The column alignment: "L" for left, "R" for right, "C" for center and the special command "X" will either **fill the column with spaces** (for colors) if ATX color is present or simply center the text if no color codes are found.If omitted, "L" for left will be used.
|`COLS("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the column. If omitted, the default value will be used.  
|`COLS("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)   | The foreground color of the column. If omitted, the default value will be used.
___

## TREE2L configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The name of the TREE2L object, for further reference.
|`CFG("ARRAY"`|           | String | The $NAME of the array / global you want to use as data source
|`CFG("HEIGHT"`|           | Number | 
|`CFG("WIDTH"`|           | Number | 
|`CFG("X"`|           | Number | 
|`CFG("Y"`|           | Number | 
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the TREE2L. If omitted, the default value will be used.   
|`CFG("BORDER")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The border color of the TREE2L. If omitted, the default value will be used.  
|`CFG("ITEM","BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the item. If omitted, the default value will be used.  
|`CFG("ITEM","FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)   | The foreground color of the item. If omitted, the default value will be used.
|`CFG("ITEM","SELBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)   | The background color of the selected item. If omitted, the default value will be used.  
|`CFG("ITEM","SELFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the selected item. If omitted, the default value will be used.
|`CFG("ITEM","CATFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the category item. If omitted, the default value will be used.
|`CFG("EVENTS","ONSELECT")`|     Y      | String  | The callback to be executed when an entry is selected. It returns the tree index in the passed parameters X and Y.
|`CFG("KEYSUSELR")`|     Y      |  Number | If set, CURSOR LEFT and CURSOR RIGHT will be used to scroll, instead of CURSOR UP and CURSOR DOWN.
|`CFG("SELALL")`|     Y      |  Number | If set, it will scroll on both CAT and SUBCAT.
___

## TEXTBOX configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The name of the TEXTBOX object, for further reference.
|`CFG("WIDTH"`|           | Number | The maximum number of character. This is also the width of the control.
|`CFG("X"`|           | Number | 
|`CFG("Y"`|           | Number | 
|`CFG("TEXT"`| Y          | String | The optional text value to pre-set the control. 
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the TEXTBOX. If omitted, the default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The border color of the TEXTBOX. If omitted, the default value will be used.  
|`CFG("DISBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the caption of the TEXTBOX when the control is disabled. If omitted, the default value will be used.   
|`CFG("DISFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the caption of the TEXTBOX when the control is disabled. If omitted, the default value will be used.  
|`CFG("TAB")`|      Y     | Number | The tab number if more text boxes are on the window. The first number must be 1.  
|`CFG("NOLR")`|      Y     | Number | If set, it will prevent CURSOR LEFT and CURSOR RIGHT keys to be processed. Handy when these keys need to be assigned to another control.  
|`CFG("EVENTS","ONCHANGE")`|      Y     | String | The optional callback to call when textbox content changes. It will append a string parameter with the textbox content.  
|`CFG("EVENTS","CHANGE")`|      Y     | String | The optional callback to call when textbox content changes. It will append two string parameters: NAME and TEXT.  
|`CFG("EVENTS","ONKEYPRESS")`|      Y     | String | The optional callback to call a key is pressed. It will append the CHAR parameter. By setting it to -1 it will cancel the operation.  
|`CFG("DISABLED"`|    Y       | Number | If set, it will render the options use the related DISFORE and DISBGND and prevent user input.
|`CFG`|    Y       | String | If set to "REFRESH" it will refresh the list box having the name equals to  CFG("NAME")
___

## CHECKBOX configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The name of the TEXTBOX object, for further reference.
|`CFG("X"`|           | Number | The X location within the client area of the current window.
|`CFG("Y"`|           | Number | The Y location within the client area of the current window.
|`CFG("CAPTION"`|           | String | The text to be displayed next to the check. This MUST contain an accelerator key to toggle it.
|`CFG("VALUE"`|     Y      | Number | 0: not selected (default), 1 is selected
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the caption of the CHECKBOX. If omitted, the default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the caption of the CHECKBOX. If omitted, the default value will be used.  
|`CFG("ACC")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the accelerator key of the CHECKBOX. If omitted, the default value will be used.  
|`CFG("CHKBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the check of the CHECKBOX. If omitted, the default value will be used.   
|`CFG("CHKFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the check of the CHECKBOX. If omitted, the default value will be used.  
|`CFG("SPACING"`|      Y     | Number | The number of spaces to render between the check and the caption. If omitted, the default value will be used.
|`CFG("KEYNOALT"`|      Y     | Number | If set, it will trap also the accelerator key without the ALT modifier.
|`CFG("EVENTS","ONCLICK"`|    Y       | String | The callback to be called when the checkbox gets clicked. It will pass also the VALUE parameter, which is TRUE is checkbox is set and FALSE if it is unchecked

___

## RADIO configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The name of the RADIO object, for further reference.
|`CFG("X"`|           | Number | The X location within the client area of the current window.
|`CFG("Y"`|           | Number | The Y location within the client area of the current window.
|`CFG("OPTIONS",n,[OPTION]`|           | [RADIO-OPTION](#radio-option-configuration) | An array of OPTIONS
|`CFG("SELECTED"`|    Y       | String | The default selected option. This is the OPTION name. If omitted, defaults to "nothing selected"
|`CFG("DISABLED"`|    Y       | Number | If set, it will render the options use the related DISFORE and DISBGND and prevent user input.
|`CFG("SPACING"`|     Y      | Number | The number of spaces to render between the option circle and the caption. If omitted, the default value will be used.
|`CFG("VSPACING"`|     Y      | Number | The number of rows to render between the options. If omitted, the default value will be used.
|`CFG("HALIGN"`|     Y      | Number | If set, it will render the options horizontally. If 0 or omitted it will render the options vertically. 
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the caption of the OPTION. If omitted, the default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the caption of the OPTION. If omitted, the default value will be used.  
|`CFG("DISBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the caption of the OPTION when the control is disabled. If omitted, the default value will be used.   
|`CFG("DISFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the caption of the OPTION when the control is disabled. If omitted, the default value will be used.  
|`CFG("ACC")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the accelerator key of the OPTION. If omitted, the default value will be used.  
|`CFG("OPTBGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the check of the OPTION. If omitted, the default value will be used.   
|`CFG("OPTFORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the check of the OPTION. If omitted, the default value will be used.  
|`CFG("EVENTS","ONSELECT")`|     Y      | String | The callback to be called when something got selected.  
___

## RADIO OPTION configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The option name
|`CFG("CAPTION"`|           | String | The option caption with accelerator (&)
___


## FRAME configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The frame name
|`CFG("X"`|           | Number | The X location within the client area of the current window.
|`CFG("Y"`|           | Number | The Y location within the client area of the current window.
|`CFG("H"`|           | Number | The height of the frame.
|`CFG("W"`|           | Number | The width of the frame.
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the caption of the OPTION. If omitted, the default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the caption of the OPTION. If omitted, the default value will be used.  
___


## SCROLLER configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The scroller name
|`CFG("ARRAY"`|           | String | Pointer to the array holding the info. Array will have a numeric subscript and content will be the displayed data.
|`CFG("X"`|           | Number | The X location within the client area of the current window.
|`CFG("Y"`|           | Number | The Y location within the client area of the current window.
|`CFG("H"`|           | Number | The height of the scroller.
|`CFG("W"`|           | Number | The width of the scroller.
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the SCROLLER. If omitted, the default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the SCROLLER. If omitted, the default value will be used.  
|`CFG("SCROLLLR"`|    Y       | Number | If set, it will scroll also LEFT and RIGHT.
|`CFG("KEYMODS"`|    Y       | String | (NOT IMPLEMENTED) Eventual key modifiers to support CTRL, ALT and SHIFT modifiers for the scrolling keys. 
|`CFG("FILTERCOLORS"`|      Y     | Number | If set, it will remove eventual color information from the array
|`CFG("FILTERBACKCOLORS"`|      Y     | Number | If set, it will remove eventual background color information from the array
|`CFG("BORDERTYPE"`|    Y       | String | If set to "H", "V" or both ("HV") it will display a border of the selected BORDER color. If omitted, it will render a scroller WITHOUT any border.
|`CFG("BORDER"`|      Y     | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the BORDER. If omitted, the default value will be used.
|`CFG("LR1000"`|      Y     | Number | If set, it will NOT scroll left and right and display the entire string.
___

## LABEL configuration
|Node |Optional  |Data type |   Description 
|---------  | :-------: | :--------:|   ----------|
|`CFG("NAME"`|           | String | The label name
|`CFG("CAPTION"`|           | String | String to be displayed.
|`CFG("X"`|           | Number | The X location within the client area of the current window.
|`CFG("Y"`|           | Number | The Y location within the client area of the current window.
|`CFG("BGND")`|     Y      | [BGND COLOR](./constants.md/#bgndground-colors)  | The background color of the LABEL. If omitted, the current (HWIN) default value will be used.   
|`CFG("FORE")`|     Y      | [FORE COLOR](./constants.md/#foreground-colors)  | The foreground color of the LABEL. If omitted, the current (HWIN) default value will be used.  
___
