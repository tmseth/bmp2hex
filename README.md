# bmp2hex

```
Author:    Robert Gallup (bg@robertgallup.com)
Date:      March 9, 2016
License:   MIT Opensource License (see license.txt) 
```

Command line Python utility to output a table of hex values representing the size and data in a bmp graphics file. This would typically be used to create graphics for display by a microprocessor, say an Arduino, on an OLED or LCD.

The _input_ is a 1-bit .bmp file (color bmp files will not work)

The _output_ is a valid C variable definition for  the Arduino. The bytes are defined as an array of const unsigned char. Since bitmaps can takea significant number of bytes, the PROGMEM keyword is used to place the data in program memory, rather than on the stack.

Results from bmp2hex.py are directed to **standard output**. You can redirect them to a file, or use cut/paste to transfer the output to your code.

### The command line is:

``` bash
$ python bmp2hex.py <infile> <tablename> [tablewidth] [sizebytes]
```

### Where:

\<_infile_\>	 = Path to input bmp file<br />
\<_tablename_\> = Name to use for the output table<br />
\[_tablewidth_\] = Width of table in infile bytes. Default = 16 (optional)<br />
\[_sizebytes_\] = Number of bytes for size (optional). 0=auto, 1 or 2 (big endian)

### Example:

``` bash
$ python bmp2hex.py soba.bmp SOBA 8 2
```

### Output:

```
const unsigned char PROGMEM SOBA [] = {
0X00, 0X28, 0X00, 0X20,
0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00,
0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00,
0X00, 0X00, 0X00, 0X80, 0X00, 0X00, 0X00, 0X01,
0X90, 0X00, 0X00, 0X00, 0X03, 0X30, 0X00, 0X00,
0X00, 0X06, 0X60, 0X00, 0X00, 0X00, 0X0C, 0XC0,
0X00, 0X00, 0X00, 0X19, 0X80, 0X00, 0X1F, 0X00,
0X33, 0X00, 0X00, 0X7B, 0XC0, 0X66, 0X00, 0X01,
0XE0, 0XF0, 0XCC, 0X00, 0X03, 0X80, 0X39, 0X98,
0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X07, 0XFF,
0XFF, 0XFF, 0XE0, 0X07, 0XFF, 0XFF, 0XFF, 0XE0,
0X07, 0XFF, 0XFF, 0XFF, 0XE0, 0X07, 0XFF, 0XFF,
0XFF, 0XE0, 0X07, 0XFF, 0XFF, 0XFF, 0XE0, 0X03,
0XFF, 0XFF, 0XFF, 0XC0, 0X03, 0XFF, 0XFF, 0XFF,
0XC0, 0X01, 0XFF, 0XFF, 0XFF, 0X80, 0X01, 0XFF,
0XFF, 0XFF, 0X80, 0X00, 0XFF, 0XFF, 0XFF, 0X00,
0X00, 0X7F, 0XFF, 0XFE, 0X00, 0X00, 0X3F, 0XFF,
0XFC, 0X00, 0X00, 0X1F, 0XFF, 0XF8, 0X00, 0X00,
0X0F, 0XFF, 0XF0, 0X00, 0X00, 0X03, 0XFF, 0XC0,
0X00, 0X00, 0X01, 0XFF, 0X80, 0X00, 0X00, 0X00,
0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00, 0X00
};
```