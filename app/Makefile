end_conv = ../tools/end_conv
make_mem = ../tools/make_mem

all: hello.o hello.lss hello.hex hello.lss1 prog_mem_content.vhd

hello.o:
	avr-gcc -Wall -Os -fpack-struct -fshort-enums -funsigned-char -funsigned-bitfields \
	-mmcu=atmega8 -DF_CPU=25000000UL -c -o"hello.o" "hello.c"
	avr-gcc -Wl,-Map,hello.map -mmcu=atmega8 -o"hello.elf"  ./hello.o  

hello.lss:
	avr-objdump -h -S hello.elf  >"hello.lss"

hello.hex:
	avr-objcopy -R .eeprom -O ihex hello.elf  "hello.hex"

hello.lss1:
	$(end_conv) < hello.lss > hello.lss1	

prog_mem_content.vhd:
	$(make_mem)  < hello.hex > ../src/prog_mem_content.vhd

clean:
	rm -fv hello.elf hello.o hello.lss* hello.hex hello.map ../src/prog_mem_content.vhd
