# Tasm-Converting-Char-to-Hexadecimal-
Using tasm this code is a converter of Char to Hexadecimal ( ASCII )

.model tiny
.code
org 100h
start:
  
     mov ah, 06h
     mov al, 00h
     mov bh, 70h
     mov cx, 0000h
     mov dx, 184fh
     int 10h
	 
	  mov ah, 02h
      mov bh, 00h
      mov dh, 00h 
      mov dl, 00h
      int 10h	

    mov ah, 09h
    mov dx, offset prompt
    int 21h

    mov ah, 07h
    int 21h
    mov bl, al
   
    mov ah, 02h
    mov dl, bl
    int 21h

    mov ah, 02h
    mov dl, 0Dh  
    int 21h
    mov dl, 0Ah  
    int 21h
    
   
    mov dx, offset result
    mov ah, 09h
    int 21h
    
    mov al, bl
    call DisplayHex
    
    
    mov ah, 4Ch
    int 21h

DisplayHex proc
    mov ah, 0
    mov cl, al
    and cl, 0F0h
    shr cl, 4
    call ConvertToHex
    mov dl, al
    mov ah, 02h
    int 21h
	
    mov cl, bl
    and cl, 0Fh
    call ConvertToHex
    mov dl, al
    mov ah, 02h
    int 21h
    ret
DisplayHex endp

ConvertToHex proc
    cmp cl, 09h
    jbe Digit
    add cl, 07h
Digit:
    add cl, 30h
    mov al, cl
    ret
ConvertToHex endp

prompt db "Input a Character: $"
result db "ASCII value is: $"

end start
