#RE 
![[Pasted image 20250612121952.png]]
We are provided with 3 files: ![[Pasted image 20250612122025.png]]
a .pdf manual of the gadget, a .bin file and a .elf file

---

Unsure exactly how to approach this problem, as I have little experience working with hardware/firmware I had ChatGPT give me suggestions as to approaches to try.

I first ran some tools to enumerate information about the `.elf` file I was investigating:

```
┌──(kali㉿kali)-[~/Downloads/re]
└─$ binwalk oled-gadget.elf                

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             ELF, 32-bit LSB executable, ARM, version 1 (SYSV)
146843        0x23D9B         ESP Image (ESP32): segment count: 8, flash mode: QUIO, flash speed: 40MHz, flash size: 1MB, entry address: 0x13037501, hash: none
359223        0x57B37         ESP Image (ESP32): segment count: 1, flash mode: QUIO, flash speed: 40MHz, flash size: 1MB, entry address: 0x36, hash: none
359288        0x57B78         ESP Image (ESP32): segment count: 1, flash mode: QUIO, flash speed: 26MHz, flash size: 1MB, entry address: 0x2dbe, hash: sha256
359310        0x57B8E         ESP Image segment count: 1, flash mode: QUIO, flash size: 32MB, entry address: 0x320001e9, hash: none
571100        0x8B6DC         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
591450        0x9065A         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
599059        0x92413         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
600414        0x9295E         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
604198        0x93826         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
608861        0x94A5D         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
610354        0x95032         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
611261        0x953BD         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
615180        0x9630C         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
635930        0x9B41A         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
637674        0x9BAEA         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
639214        0x9C0EE         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
641500        0x9C9DC         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
646533        0x9DD85         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
652491        0x9F4CB         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
663226        0xA1EBA         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
663746        0xA20C2         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
695781        0xA9DE5         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
697645        0xAA52D         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
708967        0xAD167         Unix path: /usr/lib/gcc/arm-none-eabi/10.3.1/include
715270        0xAEA06         PARity archive data - file number 19521

                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads/re]
└─$ file oled-gadget.elf 
oled-gadget.elf: ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, with debug_info, not stripped
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads/re]
└─$ readelf -h oled-gadget.elf 
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           ARM
  Version:                           0x1
  Entry point address:               0x8005c19
  Start of program headers:          52 (bytes into file)
  Start of section headers:          806152 (bytes into file)
  Flags:                             0x5000400, Version5 EABI, hard-float ABI
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         3
  Size of section headers:           40 (bytes)
  Number of section headers:         25
  Section header string table index: 24
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads/re]
└─$ readelf -S oled-gadget.elf| grep rodata
  [ 3] .rodata           PROGBITS        08005c88 015c88 000bd8 00   A  0   0  4

```

This gave us information like: oled-gadget.elf is a micro-controller with all symbols and rodata still inside, suggesting they could be statically carved.  (this suggests the information we want is in the `.rodata`)

We then carve the data we presume is associated with the image into a binary file for closer inspection:

```┌──(kali㉿kali)-[~/oled-rev]
└─$ arm-none-eabi-objcopy -O binary -j .rodata oled-gadget.elf rodata.bin
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/oled-rev]
└─$ ls
oled-gadget.elf  rodata.bin
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/oled-rev]
└─$ wc -c rodata.bin
3032 rodata.bin
```

Upon doing some research, it seemed like the most common widths for the model of oled-gadget described in the manual came in 128 and 160 columns, so I used chatgpt to generate some scripts that would generate variants of possible images from the .rodata bin for both widths until I found one that looked recognizable

```
from PIL import Image
RAW = open('rodata.bin', 'rb').read()

WIDTH = 128                       # try 160 columns (adjust if needed)
PAGES = (len(RAW) + WIDTH - 1) // WIDTH
HEIGHT = PAGES * 8

def bitrev(b): return int('{:08b}'.format(b)[::-1], 2)

for br in (False, True):          # bit-order
    for sr in (False, True):      # segment-remap
        # draw base image in page mode
        base = Image.new('1', (WIDTH, HEIGHT))
        for page in range(PAGES):
            for col in range(WIDTH):
                idx = page*WIDTH + col
                byte = RAW[idx] if idx < len(RAW) else 0
                if br: byte = bitrev(byte)
                for bit in range(8):
                    x = WIDTH - 1 - col if sr else col
                    y = page*8 + bit
                    base.putpixel((x, y), 255 if (byte >> bit) & 1 else 0)

        for rot in (0, 90, 180, 270):
            img = base.rotate(rot, expand=True)
            img.save(f"out_br{int(br)}sr{int(sr)}rot{rot}.png")
            print("wrote out_br%d_sr%d_rot%d.png" % (br, sr, rot))
```

Among the variants generated was this:
![[Pasted image 20250612123753.png]]

Which clearly depicts the flag: `SVUSCG{Gen3-BestGen}`