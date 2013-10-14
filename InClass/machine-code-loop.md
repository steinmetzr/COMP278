Python program

	sum = value
	while True:
		sum += 1

Basic equivalent

	10 sum = value
	20 sum = sum + 1
	30 goto 20

Assembly equivalent

	LOAD R1, 0xff # put value there
	LOAD R2, 0xfe # put 1 at that location
	ADD  R1, R2, R1
	JZE  R0, mmm

Machine code equivalent

Study cpu-16bit-isa.md to convert the assembly above to machine code.