# tsdz2_hallsensor
How to update your stock firmware to have hall sensor data instead of battery level.

Limited warranty: "How to update your stock firmware to have hall sensor data instead of battery level" and documentation are "as is" without any warranty. The licensee assumes the entire risk as to the quality and performance of the software. In no event shall "How to update your stock firmware to have different factory default Max Speed, Wheel Size and Assist Level" or anyone else who has been involved in the creation, development, production, or delivery of this software be liable for any direct, incidental or consequential damages, such as, but not limited to, loss of anticipated profits, benefits, use, or data resulting from the use of this software, or arising out of any breach of warranty.

Based on ideas from casainho and hurzhurz found here: https://endless-sphere.com/forums/viewtopic.php?f=28&t=94351&hilit=TSDZ2

Original - calculated battery level goes to $76:
```
0x9f0a:	bb af   add A, $af
0x9f0c:	b7 76   ld $76,A
```

New - $0C goes to $76:
```
0x9f0a:	b6 0C	  ld A, $0C
0x9f0c:	b7 76   ld $76,A
```

$76 is the 2nd value in the UART message to display. Originally it contains the battery level.
$0C holds the hall sensor data. The above patch will send this instead of the battery level.
