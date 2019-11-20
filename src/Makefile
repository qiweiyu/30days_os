TARGET=os.img
SYSFILE=haribote.sys

default:$(TARGET)

$(TARGET): ipl.o $(SYSFILE)
	mformat -f 1440 -C -B $< -i $(TARGET) ::
	mcopy $(SYSFILE) -i $(TARGET) ::

$(SYSFILE): asmhead.o bootpack.bin
	cat $^ > $@

bootpack.bin: stdio.o int.o graphic.o dsctbl.o asmfunc.o bootpack.o
	ld -m elf_i386 -T os.ld $^ -o $@

%.o: %.c
	gcc -w -c -m32 -nostdlib -fno-pie $*.c -o $*.o

%.o: %.asm
	nasm $*.asm -o $*.o

asmfunc.o: asmfunc.asm
	nasm -f elf $< -o $@

clean:
	rm *.bin *.sys *.img *.o
