CFLAGS = -c -Wall
CC = gcc
LIBS =  -lm 


all: scanner

scanner: scanner.o reader.o charcode.o token.o error.o
	${CC} scanner.o reader.o charcode.o token.o error.o -o scanner

reader.o: reader.c
	${CC} ${CFLAGS} reader.c

scanner.o: scanner.c
	${CC} ${CFLAGS} scanner.c

charcode.o: charcode.c
	${CC} ${CFLAGS} charcode.c

token.o: token.c
	${CC} ${CFLAGS} token.c

error.o: error.c
	${CC} ${CFLAGS} error.c

test: scanner
	@for i in 1 2 3 4 5 6 7; do \
        echo "Running test $$i..."; \
        ./scanner ../test/example$$i.kpl > ../test/output/output$$i.txt; \
        if diff -q ../test/output/output$$i.txt ../test/real_result/result$$i.txt > /dev/null; then \
            echo "Test $$i PASSED"; \
        else \
            echo "Test $$i FAILED"; \
        fi; \
    done
clean:
	rm -f *.o *~

