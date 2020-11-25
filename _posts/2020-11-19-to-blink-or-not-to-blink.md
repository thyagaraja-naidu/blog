---
layout: post
author: Thyagaraja Naidu
title: To blink or not to blink :)
---

## HW Platform to be used
### Microchip(formerly ATMEL) 328P Controller

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This post is yet another blinky program on popular Microchip ATMEGA 328p micro controller. We will be using  [Arduino nano](https://store.arduino.cc/arduino-nano) board for our experiment. Since the HW is readily available we can concentrate on writing our first program for blinking the LED!

### Software development environment for blinky
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We will be using Bare metal programming technic to program the microcontroller. we will need below tools for the development.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I will be uning __Zorin OS__, which is a linux distribution based on ubuntu platform. You can download a copy of this linux flavour [here](https://zorinos.com/) for free :blush:
Instructions given in this blog should work on most of the ubuntu flavoured OSs.

1. Compiler
2. Programmer software
3. Your favourite code editor!

### Tool setup
#### AVR GCC Compiler 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We will be using AVR GCC compiler which is based on a open source compiler developed by free software foundation(FSF). Full form of GCC is __GNU Compiler Collection__. GCC compiler can used for many languages like, C, C++ etc.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Goto Microchip website and [download](https://www.microchip.com/mplab/avr-support/avr-and-arm-toolchains-c-compilers) latest version of AVR GCC compiler for linux. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;If you need to check whether your linux OS is 32bit or 64bit you can execute below command.

> $ uname -m
>    <br />x86_64


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;So, i will be downloading 64bit avr-gcc toolchain [AVR 8-bit Toolchain 3.6.2 - Linux 64-bit](https://www.microchip.com/mymicrochip/filehandler.aspx?ddocname=en607660), which is latest(and greatest), at the time of this writing.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Let's install the downloaded setup file 'avr8-gnu-toolchain-3.6.2.1778-linux.any.x86_64.tar.gz' in linux now. Below set of commands will install the avr-gcc compiler on your PC.

> tar -xzf avr8-gnu-toolchain-3.6.2.1778-linux.any.x86_64.tar.gz

Update the PATH variable to AVR-GCC tool folder
> $ nano ~/.bashrc

**!!! Beware, you will break the bash command execution if you overwrite PATH variable!!!** 

add at the end of the file to update PATH variable with avr-gcc compiler path 
> export PATH=$PATH:/home/tools/avr8-gnu-toolchain-linux_x86_64/bin/

A quick check for avr-gcc version can now be done.
> $ avr-gcc --version
>    <br />avr-gcc (AVR_8_bit_GNU_Toolchain_3.6.2_1778) 5.4.0
>    <br />Copyright (C) 2015 Free Software Foundation, Inc.
>    <br />This is free software; see the source for copying conditions.  There is NO
>    <br />warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Rejoice, your avr-gcc compiler set up is now complete :)

#### AVR Libc & Binutils

Unfortunately, we can not use the compiler installation we did just now! We need to still install [avr-libc](https://www.nongnu.org/avr-libc/) & [avr-binutils](https://www.archlinux.org/packages/community/x86_64/avr-binutils/)

avr libc provides c runtime libraries for AVR controllers. Binutils is binary utilities to handle AVR binary files.

> $ sudo apt-get install avr-libc binutils-avr

#### AVR Programmer utility: AVRDUDE
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We need a programmer software to burn our compiled program into AVR chips. We will be using avrdude software for this. Installation is fairly simple and straight forward. you can install avr dude using below command in terminal.
> $ sudo apt-get install avrdude

#### Your favourite code editor!
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Last but not least, we need a editor program to write our programs. i will be using **visual studio code**. Code is a free SW editor developed by Microsoft with open source license. Instaltion procedure is given below on ubuntu.

* goto --> Code download [link](https://code.visualstudio.com/Download)
* Download __Code.deb__ package for ubuntu. you also have installer files for other OS's on the same link.
* Install MS code with below command
  * > $ sudo dpkg -i code_1.51.1-1605051630_amd64.deb
* MS code is installed now. Close the terminal.


![800x600](https://i.picsum.photos/id/688/800/600.jpg)

## Some great heading (h2)

Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu.

Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Another great heading (h2)

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit.

### Some great subheading (h3)

Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum.

Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc.

### Some great subheading (h3)

Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

> This quote will change your life. It will reveal the secrets of the universe, and all the wonders of humanity. Don't misuse it.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt.

### Some great subheading (h3)

Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum.

```html
<html>
  <head>
  </head>
  <body>
    <p>Hello, World!</p>
  </body>
</html>
```


In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

#### You might want a sub-subheading (h4)

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

#### But it's probably overkill (h4)

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

##### Could be a smaller sub-heading, `pacman` (h5)

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

###### Small yet significant sub-heading  (h6)

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

### Oh hai, an unordered list!!

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

- First item, yo
- Second item, dawg
- Third item, what what?!
- Fourth item, fo sheezy my neezy

### Oh hai, an ordered list!!

In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris.

1. First item, yo
2. Second item, dawg
3. Third item, what what?!
4. Fourth item, fo sheezy my neezy



## Headings are cool! (h2)

Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc.

### Tables

Title 1               | Title 2               | Title 3               | Title 4
--------------------- | --------------------- | --------------------- | ---------------------
lorem                 | lorem ipsum           | lorem ipsum dolor     | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit


Title 1 | Title 2 | Title 3 | Title 4
--- | --- | --- | ---
lorem | lorem ipsum | lorem ipsum dolor | lorem ipsum dolor sit
lorem ipsum dolor sit amet | lorem ipsum dolor sit amet consectetur | lorem ipsum dolor sit amet | lorem ipsum dolor sit
lorem ipsum dolor | lorem ipsum | lorem | lorem ipsum
lorem ipsum dolor | lorem ipsum dolor sit | lorem ipsum dolor sit amet | lorem ipsum dolor sit amet consectetur