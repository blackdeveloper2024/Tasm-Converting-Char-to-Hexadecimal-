# Tasm-Converting-Char-to-Hexadecimal-
Using tasm this code is a converter of Char to Hexadecimal ( ASCII )

This are how it process

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








