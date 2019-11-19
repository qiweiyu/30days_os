OUTPUT_PATH=target
IPL_NAME=ipl
IMG_NAME=os
SYS_NAME=haribote
ASM_HEAD=asmhead
BOOT_PACK=bootpack
OS_LINKERSCRIPT=os.ld
ASM_FUNC=asmfunc

default: $(IPL_NAME) $(SYS_NAME)
	mformat -f 1440 -C -B $(OUTPUT_PATH)/$(IPL_NAME).bin -i $(OUTPUT_PATH)/$(IMG_NAME).img ::
	mcopy $(OUTPUT_PATH)/$(SYS_NAME).sys -i $(OUTPUT_PATH)/$(IMG_NAME).img ::

$(IPL_NAME):
	nasm $(IPL_NAME).asm -o $(OUTPUT_PATH)/$(IPL_NAME).bin

$(ASM_HEAD):
	nasm $(ASM_HEAD).asm -o $(OUTPUT_PATH)/$(ASM_HEAD).bin

$(ASM_FUNC):
	nasm -f elf $(ASM_FUNC).asm -o $(OUTPUT_PATH)/$(ASM_FUNC).o

$(SYS_NAME): $(ASM_HEAD) $(ASM_FUNC)
	gcc -m32 -nostdlib -fno-pie -T $(OS_LINKERSCRIPT) $(BOOT_PACK).c $(OUTPUT_PATH)/$(ASM_FUNC).o -o $(OUTPUT_PATH)/$(BOOT_PACK).bin
	cat $(OUTPUT_PATH)/$(ASM_HEAD).bin $(OUTPUT_PATH)/$(BOOT_PACK).bin > $(OUTPUT_PATH)/$(SYS_NAME).sys
