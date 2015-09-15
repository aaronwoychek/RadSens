CFLAGS=-Wall -g

flash: avrTx.hex
	avrdude -c atmelice_isp -p attiny2313 -e -U flash:w:avrTx.hex

hex: avrTx.hex

avrTx.hex: avrTx.elf
	avr-objcopy -j .text -j .data -O ihex avrTx.elf avrTx.hex

avrTx.elf: avrTx.o nrf24.o radioPinFunctions.o

	avr-gcc -o avrTx.elf avrTx.o nrf24.o radioPinFunctions.o

avrTx.o: avrTx.c

	avr-gcc -mmcu=attiny2313 -Os -c avrTx.c

nrf24.o: nrf24/nrf24.c

	avr-gcc -mmcu=attiny2313 -Os -c nrf24/nrf24.c

radioPinFunctions.o: nrf24/radioPinFunctions.c

	avr-gcc -mmcu=attiny2313 -Os -c nrf24/radioPinFunctions.c

clean:
	rm -f avrTx.elf avrTx.hex radioPinFunctions.o nrf24.o avrTx.o
