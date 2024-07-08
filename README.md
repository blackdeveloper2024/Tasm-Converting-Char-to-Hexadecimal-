# Tasm-Converting-Char-to-Hexadecimal-
Using tasm this code is a converter of Char to Hexadecimal ( ASCII )

Using this as a process

    mov cl, bl
    and cl, 0Fh
    call ConvertToHex
    mov dl, al
    mov ah, 02h
    int 21h
    ret








