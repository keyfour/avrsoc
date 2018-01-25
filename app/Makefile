
all: hello.o hello.lss hello.hex

hello.o:
	avr-gcc -Wall -Os -fpack-struct -fshort-enums -funsigned-char -funsigned-bitfields \
	-mmcu=atmega8 -DF_CPU=25000000UL -c -o"hello.o" "hello.c"
	avr-gcc -Wl,-Map,hello.map -mmcu=atmega8 -o"hello.elf"  ./hello.o  

hello.lss:
	avr-objdump -h -S hello.elf  >"hello.lss"

hello.hex:
	avr-objcopy -R .eeprom -O ihex hello.elf  "hello.hex"

clean:
	rm -fv hello.elf hello.o hello.lss* hello.hex hello.map
