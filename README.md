# MONOCHROMATIC GRAPHICAL LCD
The monochromatic GLCD used is JHD12864. The datasheet can be downloaded from
http://cnpdf.alldatasheet.com/datasheet-pdf/view/276158/JHD/JHD12864G.html.

You will require AVRLib which can be downloaded from
http://linux.softpedia.com/progDownload/AVR-Libc-Download-7401.html and unzipped. The MCU used is an

ATMega16 or ATMega32.
Open AVRStudio4. From __File->New__ create a project named GLCD. Choose the location for your project (I choose
C:\Desktop). Follow the normal steps as in WinAVR till your Project window is opened. Your source files contain
only one file GLCD.c.

Open AVRLib __Copy & Paste__ glcd.c and glcd.h files to your project folder(C:\Desktop\GLCD).Now __Drag & Drop__ glcd.c
to the __Source files__ and glcd.h to the __Header files. Compile__ the file. Some errors will be shown in the __Build__ box
indicating that some files doesn't exist with some other errors.

Just drag and drop the files which don’t exist in the same way as glcd.c and glcd.h while ignoring other errors.

The files you have to include are global.h, ks0108.h, ks0108conf.h, ks0108.c, avrlibdefs.h, avrlibtypes.h, font5x7.h,
fontgr.h, glcd.c, glcd.h.

Open __ks0108conf.h__ and you will find statements such as:


__#ifndef GLCD_CTRL_PORT__

__#define GLCD_CTRL_PORT           PORTA // PORT for LCD control signals__

__#define GLCD_CTRL_DDR         DDRA // DDR register of LCD_CTRL_PORT__

__#define GLCD_CTRL_RS             PA4 // pin for LCD Register__

This shows you the corresponding connections to be made between the GLCD and MCU. For ex. GLCD_CTRL_RS
PA4 means connect RS (PIN 4 of GLCD) to PINA4 of MCU. You can configure the ports as you wish. Some changes
to be done, __CS0__ and __CS1__ have to be treated as __CS1__ and __CS2__ of GLCD. __D/I__ have to be treated as __RS__, while CS2 and
CS3 don’t exist in the GLCD to be connected. You can delete the statements of CS2 and CS3 and use the MCU pins
for other purposes.

___

#### In the GLCD.c file write the following program for checking GLCD:
```
#include <avr/io.h>
#include "glcd.h"
#include "ks0108.h"
int main(void)
{
glcdInit();
glcdPutStr("The GLCD is working");
}
```
___
![Screenshot (130)](https://user-images.githubusercontent.com/64007722/79957168-d1561400-849e-11ea-86d2-dff0a3585031.png)
___
