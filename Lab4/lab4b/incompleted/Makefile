CFLAGS = -c -Wall
CC = gcc
LIBS =  -lm 

all: kplc

kplc: main.o parser.o scanner.o reader.o charcode.o token.o error.o symtab.o semantics.o debug.o instructions.o codegen.o
	${CC} main.o parser.o scanner.o reader.o charcode.o token.o error.o symtab.o semantics.o debug.o instructions.o codegen.o -o kplc

main.o: main.c
	${CC} ${CFLAGS} main.c

scanner.o: scanner.c
	${CC} ${CFLAGS} scanner.c

parser.o: parser.c
	${CC} ${CFLAGS} parser.c

reader.o: reader.c
	${CC} ${CFLAGS} reader.c

charcode.o: charcode.c
	${CC} ${CFLAGS} charcode.c

token.o: token.c
	${CC} ${CFLAGS} token.c

error.o: error.c
	${CC} ${CFLAGS} error.c

symtab.o: symtab.c
	${CC} ${CFLAGS} symtab.c

semantics.o: semantics.c
	${CC} ${CFLAGS} semantics.c

debug.o: debug.c
	${CC} ${CFLAGS} debug.c

instructions.o: instructions.c
	${CC} ${CFLAGS} instructions.c

codegen.o: codegen.c
	${CC} ${CFLAGS} codegen.c

clean:
	rm -f *.o *~
	
test:
	@for i in 1 2 3 4; do \
		echo "Compiling example$$i..."; \
		./kplc ../tests/example$$i.kpl ../tests/output/example$$i.out -dump \
			> ../tests/output/output$$i.txt; \
		if diff -q ../tests/example$$i ../tests/output/example$$i.out > /dev/null; then \
			echo "Example $$i PASSED"; \
		else \
			echo "Example $$i FAILED"; \
		fi; \
	done



