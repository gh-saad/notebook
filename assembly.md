# Assembly Language

## Registers

### Types of Registers

#### General Purpose (Input, Output and Move value from reg to reg)

* ##### Accmulator

  * al [size: 8 bit low, use: input]    1 byte [1,2,3,4,5,6,7,8]
  * ah [size: 8 bit high, use: output]  1 byte [9,10,11,12,13,14,15,16]
  * ah (2 for char, 9 for string)
  * ax [size: 16 bit, use: move value]  2 byte [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16]
  * Eax [size: 32 bit]
  * Rax [size: 64 bit]

* ##### Data

  * dl [size: 8 bit low, use: for output value much be in it]
  * dh [size: 8 bit low, use: for output value much be in it]
  * dx [size: 16 bit, use: for output value much be in it]

* ##### Base

  * bl [size: 8 bit low, use: Store Value when other is occupied]
  * bh [size: 8 bit high, use: Store Value when other is occupied]
  * bx [size: 16 bit, use: Move]
  * Ebx [size: 32 bit]
  * Rbx [size: 64 bit]

* ##### Counter

  * cl [size: 8 bit low, use: loop iteration]
  * ch [size: 8 bit high, use: loop iteration]
  * cx [size: 16 bit, use: loop iteration] ; mostly used

* #### Segment

  * Code Segment
    * cs
  * Data Segment
    * ds
  * Stack Segment
    * ss
  * Extra Segment
    * ex
  * Index Registers
    * Source Index
    * Distination Index
  * Special Registor
    * Intertion pointer
    * .Stack Pointer

* #### Flag Registor

  * comming soon

## How to Start coding

Install and open dosbox and then type this to mount C Drive

    mount c c:/MP
    c:

## Edit or Create File

    edit file_name.asam

## Basic Structure

```asm
dosseg       ;Format
.model small ;take space in RAM 
             ;[small, medium, compate, large, huge, directive]
.stack 100h  ;Use when we need to use the occupied 
             ;register we can push that value to the stack
.data        
    ;Define all variables here
.code 
Main proc
    ;coding here
mov ah,4ch
int 21h
Main endp
end Main
 ```

### Send Interput to CPU

    int 21h

## How to Run

Save and Exit file then write these cmd one by one

```bash
masm file_name.asm;
link file_name.obj;
file_name.exe
```

## Print single char

    mov dx,'a' ;initilizae 'a' to dx register
    mov ah,2   ;Output char Intrupt
    int 21h    ;Send Intrupt

## Input and Output char

    mov ah,1  ;Take input
    int 21h   ;Send Intrupt
    mov dl,al ;Move value to Dl register so,ah can ouput
    mov ah,2  ;Output char Intrupt
    int 21h   ;Send Intrupt

## Add two numbers

    mov al,4
    mov dl,3
    add dl,al
    add dl,48
    mov ah,2
    int 21h

## Sub two numbers

    mov al,3
    mov dl,4
    sub dl,al
    add dl,48
    mov ah,2
    int 21h

### Add this to convert hexcode to descimal

    add reg,48
### Enter Key Code

    mov dx,10
    mov ah,2
    int 21h
    mov dx,13
    mov ah,2
    int 21h

## Variables

### Syntax

    varName varSize value

#### Example

    varName db "x"

#### Size

* db 8 bits
* dw 16 bits
* dd 32 bits
* dq 64 bits
* dt 80 bits

#### Values

* int: must be in Ascii code
* char: '0'
* str: 'stringValue$' must end on $

### Initilization

    var1 db ?
    var2 db 'saad$'

### Accessing var

Accessing variables in .code body these two lines required

    mov ax,@data
    mov ds,ax

### Print char

    ; for char
    mov dx,var1
    mov ah,2
    int 21h
    ; for string
    mov dx,offset var2  ;lea dx,var2
    mov ah,9
    int 21h

## Defination

    ; coming soon

## Loop

### Syntext

    mov cx,{number}   ; counter Register
    loopName:
        ; Code here
    loop loopName

### Increment

    add dx,1 
    ; or
    lnc dx

### Example

    mov cx,10      ; counter register for loop counter
    mov bx,48      ; 48 ASCII Code for 0
    L1:
        mov dx,bx
        mov ah,2
        int 21h
        add bx,1    ; Increment
    loop L1

## Jump

    Jmp1:
        ; Code
    cmp register1,register1 
    je Jmp2


    Jmp2:
        ; Code
    cmp register1,register1 
    je Jmp1

    ;other coding

## Stack

    mov al,2
    push ax [16 bit]
    pop ax [16 bit]
    mov dx,ax
    mov ah,2
    int 21h

## nested loop

    mov cx,5 ; L1
    mov bx,5 ; L2
    l1:
        push cx     ; move to stack
        mov cx,bx
        L2:
            ;code
        Loop L2
        inc bx ; l2
        pop cx
    Loop L1

## Procedure

    Name proc
        ; Code
        ret
    Name endp

## Macro

    Name macro param1
        ; Code
    endm

