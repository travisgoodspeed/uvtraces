

run:

#Make the dumps.
	for number in `seq 1 6000`; do \
		echo $$number ; \
		sleep 1 ; \
		minipro -p PIC16C74 -r `date "+%Y%m%d-%H%M%S"`.bin ; \
		hd `ls 202*.bin | tail -n 1` ; \
	done

zero:
#Zero the chip.
	dd if=/dev/zero of=zero.bin bs=1024 count=8
	minipro -p PIC16C74 -w zero.bin
	rm -f zero.bin

