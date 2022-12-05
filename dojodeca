//ex 7
----------------------------------------------------------------------------------------------------
section .data
	 msg db "The two digit Hex Number is", 10
	 msglen equ $-msg
	 num1 db 23H

section .bss
	sum resb 1
	temp resb 1	
	
section .text
global _start
_start:
         mov rax,1         	
         mov rdi,1 
         mov rsi,msg 
         mov rdx,msglen  
         syscall
         
mov al,byte[num1]         
mov byte[sum],al   
mov bp,2	 ; bp=2
up:rol al,4 

      mov bl,al  ; al= 32h
      and al,0Fh ;  al= 02h
      cmp al,09;  
      jbe down
     add al,07h
down:Add al, 30h ; al=32h
      Mov byte[temp],al 
      
      mov rax,1         	 
      mov rdi,1  
      mov rsi,temp 
      mov rdx, 1  
      syscall	

     mov al,bl ; bl=23h
     dec bp
     jnz up
     
mov rax,60    
mov rdi,0      
syscall


//---------------------------------------------------------------------------
//ex 9
section .data
    msg db "Enter name!", 0ah
        db "Enter panel"
    msglen equ $-msg
    
    msg1 db "Name  and Panel is", 0ah
    msglen1 equ $-msg1
    
    newline db 10
    
section .bss
nameandpanel resb 15
name_len resq 1
ans resb 1

section .text
    global _start

_start:
    mov rax, 1            ;Give msg to enter name and panel
    mov rdi, 1
    mov rsi, msg
    mov rdx, msglen
    syscall
    
    mov rax,0         	  ; Take input of name and panel
    mov rdi,0 
    mov rsi,nameandpanel 
    mov rdx,15  
    syscall		 
    mov [name_len],rax
    
    mov rax, 1            ;display  msg name and panel is
    mov rdi, 1
    mov rsi, newline
    mov rdx, 1
    syscall
    
    mov rax, 1            ;display  msg name and panel is
    mov rdi, 1
    mov rsi, msg1
    mov rdx, msglen1
    syscall
    
    mov rax, 1            ;actual dispaly
    mov rdi, 1
    mov rsi, nameandpanel
    mov rdx, 10
    syscall 
    
   
    mov rax, 60
    mov rdi, 0
    syscall
    
    
    
    //ex add nums
    ---------------------------------------------------------------------------------------------------------------------
  %macro read 4
    mov rax,%1
    mov rdi,%2
    mov rsi,%3
    mov rdx,%4
	syscall
%endmacro

section .data

	msg db 10,"Enter the 8 bit number "
	msglen equ $-msg
	msg1 db 10, "the result is"
	msglen1 equ $-msg1
	count db 2
	NL db 10

section .bss

	num1 resb 3
	num2 resb 3
	temp resb 2

section .text

global _start

_start:
	read 1,1,msg,msglen
	read 0,0,num1,3
	read 1,1,msg,msglen
	read 0,0,num2,3

	mov al,[num1]
	cmp al,39H
	jbe skip
	sub al,07H
skip:   sub al,30H
	rol al,4
	mov bl,[num1+1]
	cmp bl,39H
	jbe skip1
	sub bl,07H
skip1:  sub bl,30H
	add al,bl
	mov [num1],al


	mov al,[num2]
	cmp al,39H
	jbe skip2
	sub al,07H
skip2:  sub al,30H
	rol al,4
	mov bl,[num2+1]
	cmp bl,39H
	jbe skip3
	sub bl,07H
skip3:  sub bl,30H
	add al,bl
	mov [num2],al

	read 1,1,msg1,msglen1

	mov al,[num1]
	add al,[num2]
up:	rol al,4
	mov bl,al
	and al,0FH
	CMP AL,09h
	jbe skip4
	add al,07H
skip4:  add al,30H
	mov [temp],al
	read 1,1,temp,1
	mov al,bl
	dec byte[count]
	jnz up	

	read 1,1,NL,1
	read 60,0,0,0




  
	read 1,1,NL,1
	read 60,0,0,0
 
 ----------------------------------------------------------
 // addition hardcode
 section .data
	msg db 'The sum is:',10   
	msgLen  equ $-msg    
	num1 db  11H
	num2 db  22H 
	
section .bss
	sum resb 1
	temp resb 1			
 
section .text
global _start 
_start:
         mov rax,1         	
         mov rdi,1 
         mov rsi,msg 
         mov rdx, msgLen  
         syscall		 	                    
mov al,byte[num1]        
add al,byte[num2]                  
mov byte[sum],al   
mov bp,2
up:rol al,4  
   mov bl,al
   and al,0Fh 
   cmp al,09 
    jbe down
     add al,07h
    down:Add al, 30h
      Mov byte[temp],al 
       mov rax,1         	 
      mov rdi,1  
      mov rsi,temp 
      mov rdx, 1  
       syscall	
      mov al,bl ; AL = 7AH =  07A, 0AH
     dec bp
     jnz up
mov rax,60    
mov rdi,0      
syscall
	
