MVI A, 40H        ; Reset 8251
OUT 81H

MVI A, 4EH        ; Mode instruction
OUT 81H

MVI A, 37H        ; Enable transmitter and receiver
OUT 81H

; Transmission
MVI A, 41H        ; ASCII 'A'
OUT 80H           ; Transmit character

; Reception
WAIT: IN 81H      ; Read status
ANI 02H           ; Check RxRDY
JZ WAIT           ; Wait until character is received

IN 80H            ; Read received character
STA 2050H         ; Store received character

HlT
Transmitted Character : A
Received Character    : A

Memory Location 2050H : 41H
