# Start code:
    mount c c:/MP
    c:

# New/open File:
    edit file_name.asam

# Basic Structure:
    dosseg (Format)
    .model small (Use to take space i RAM) [small, medium, compate, large, huge, directive]
    .stack 100h (Use when we need to use the occupied register we can push that value to the stack string revirce)
    .data (Define variable after that)

    .code (after main coding start)
    Main proc
        ;coding here
    mov ah,4ch
    int 21h
    Main endp
    end Main

# Registers
    ## Types of Registers
    1 General Purpose (Input, Output and Move value from reg to reg)
        a. Accmulator  
            al [size: 8 bit low, use: input]    1 byte [1,2,3,4,5,6,7,8] 
            ah [size: 8 bit high, use: output]  1 byte [9,10,11,12,13,14,15,16] ; ah(2 for char,9 for string)
            ax [size: 16 bit, use: move value]  2 byte [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16]
            Eax [size: 32 bit]
            Rax [size: 64 bit]
        b. Base
            bl [size: 8 bit low, use: Store Value when other is occupied] 
            bh [size: 8 bit high, use: Store Value when other is occupied]
            bx [size: 16 bit, use: Move]
            Ebx [size: 32 bit]
            Rbx [size: 64 bit]
        c. Counter
            cl [size: 8 bit low, use: loop iteration]
            ch [size: 8 bit high, use: loop iteration]
            cx [size: 16 bit, use: loop iteration] ; mostly used
        d. Data
            dl [size: 8 bit low, use: for output value much be in it]
            dh [size: 8 bit low, use: for output value much be in it]
            dx [size: 16 bit, use: for output value much be in it] 

    2. Segment 
        a. Code Segment
            cs
        b. Data Segment
            ds
        c. Stack Segment 
            ss
        d. Extra Segment
            ex
    3. Index Registers
        a. Source Index
        b. Distination Index
    4. Special Registor
        a.Intertion pointer
        b.Stack Pointer
    5. Flag Registor
    6. Base Registor

#Send Interput to CPU   
    int 21h

# Run
save and exit file
masm file_name.asm;
link file_name.obj;
file_name.exe

# Print single char
mov dx,'a'
mov ah,2
int 21h

# Input and Output char
mov ah,1
int 21h
mov dl,al
mov ah,2
int 21h

# add two number
mov al,4
mov dl,3
add dl,al
add dl,48
mov ah,2
int 21h

# Sub 
mov al,3
mov dl,4
sub dl,al
add dl,48
mov ah,2
int 21h

# when number add
add reg,48

# Variables 
    varName varSize value
    e.g:
        varName db "x"
    size: 
        db 8 bits
        dw 16 bits
        dd 32 bits
        dq 64 bits
        dt 80 bits
    value:
        int: must be in Ascii code
        char: '0'
        str: 'stringValue$'

    # Initilization
        var1 db ?
        var2 db 'saad$'
    
    # Accessing var
        mov ax,@data
        mov ds,ax
    # Print char
        mov dx,var1
        mov ah,2
        int 21h
    # Print string
        mov dx,offset var2 | lea dx,var2
        mov ah,9
        int 21h
    # Defination
        ; coming soon
# Loop
    ## Syntext:
        mov cx,number   ; counter Register
        loopName:
            ; Code here
        loop loopName

        # increment
            add dx,1 | lnc dx
    # code
        mov cx,10
        mov bx,48
        L1:
            mov dx,bx
            mov ah,2
            int 21h
            add bx,1
        loop L1

# Jump
    Jmp1:
        ; Code
    cmp register1,register1 
    je Jmp2


    Jmp2:
        ; Code
    cmp register1,register1 
    je Jmp1

    ;other coding

#stack
    mov al,2
    push ax [16 bit]
    pop ax [16 bit]
    mov dx,ax
    mov ah,2
    int 21h

#nested loop
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

#procedure
    Name proc
        ; Code
        ret
    Name endp

#macro 
    Name macro param1
        ; Code
    endm 

# Enter Key Code:
    mov dx,10
    mov ah,2
    int 21h
    mov dx,13
    mov ah,2
    int 21h

.data
msg1 db "gg$"

.code
main proc
mov ax,@data
mov ds,ax
mov dx,offset msg1
mov ah,9
int 21h