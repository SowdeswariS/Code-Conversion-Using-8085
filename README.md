# Code-Conversion-Using-8085
## Aim:
## To write 8085 microprocessor programs for converting:
1.	Hexadecimal to ASCII
2.	ASCII to Hexadecimal
## Apparatus Required:
•	Laptop with an internet connection
## Program 1: Hexadecimal to ASCII Conversion
## Algorithm:
1.	Load the hexadecimal number from memory location 4200H.
2.	Mask the upper nibble and check if it is less than 10H.
3.	If it is less than 10H, add 30H to convert it to ASCII.
4.	If it is greater than 10H, add 37H to convert it to ASCII.
5.	Repeat the process for the lower nibble.
6.	Store the ASCII equivalent in memory location 4300H and 4301H.

## program:
; Program: Convert Hexadecimal (0–9, A–F) to ASCII
; Input  : Hex digit at 2050H
; Output : ASCII code stored at 2051H

LDA 2050H        ; Load hex number into Accumulator
CPI 0AH          ; Compare with 0AH (10 decimal)
JC DIGIT         ; If < 0AH, it's 0–9
ADI 37H          ; Else add 37H → converts A–F to ASCII ('A'=41H)
JMP STORE

DIGIT: 
ADI 30H          ; Add 30H → converts 0–9 to ASCII ('0'=30H)

STORE: 
STA 2051H        ; Store ASCII code at 2051H
HLT

## Output:
•	The ASCII equivalent of the hexadecimal number will be stored in 4300H (upper nibble) and 4301H (lower nibble).
<img width="1001" height="502" alt="Screenshot 2025-09-26 132743" src="https://github.com/user-attachments/assets/8da29070-c760-4d93-b906-1a0f209e0998" />


## Program 2: ASCII to Hexadecimal Conversion
## Algorithm:
1.	Load the first ASCII digit from memory location 4200H.
2.	Convert it to hexadecimal by subtracting 30H (if it's a number) or 37H (if it's a letter A-F).
3.	Load the second ASCII digit from memory location 4201H and repeat the process.
4.	Combine the upper and lower nibbles to form a hexadecimal number.
5.	Store the result in memory location 4300H.

## program:
; Program: Convert ASCII code to Hexadecimal
; Input  : ASCII at 2050H
; Output : Hex value stored at 2051H

LDA 2050H        ; Load ASCII character into accumulator
CPI 3AH          ; Compare with 3AH ('9'+1)
JC DIGIT         ; If < 3AH → '0'–'9'
SUI 37H          ; Else subtract 37H → converts 'A'–'F' to 0AH–0FH
JMP STORE

DIGIT: 
SUI 30H          ; Subtract 30H → converts '0'–'9' to 00H–09H

STORE: 
STA 2051H        ; Store hex result at 2051H
HLT

## Output:
•	The hexadecimal equivalent of the ASCII input will be stored in memory location 4300H.
<img width="1181" height="456" alt="Screenshot 2025-09-26 134033" src="https://github.com/user-attachments/assets/a4b9a315-4517-44c3-9e55-2d6e46ad9785" />

## Result:
The 8085 microprocessor successfully converts hexadecimal numbers to ASCII and vice versa, storing the results in memory.
