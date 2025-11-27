CFLAGS = -c -Wall
CC = gcc
LIBS =  -lm 

all: parser

parser: main.o parser.o scanner.o reader.o charcode.o token.o error.o
	${CC} main.o parser.o scanner.o reader.o charcode.o token.o error.o -o parser

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

test: parser
	@for i in 1 2 3 4 5 6 7; do \
		echo "Running test $$i..."; \
		./parser ../test/example$$i.kpl > ../test/output/output$$i.txt; \
		if diff -q ../test/output/output$$i.txt ../test/result$$i.txt > /dev/null; then \
			echo "Test $$i PASSED"; \
		else \
			echo "Test $$i FAILED"; \
		fi; \
	done

clean:
	rm -f *.o *~

