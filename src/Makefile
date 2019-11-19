default: ipl haribote
	mformat -f 1440 -C -B target/ipl.bin -i target/os.img ::
	mcopy target/haribote.sys -i target/os.img ::

ipl:
	mkdir -p target
	nasm ipl.asm -o target/ipl.bin

haribote:
	mkdir -p target
	nasm haribote.asm -o target/haribote.sys
