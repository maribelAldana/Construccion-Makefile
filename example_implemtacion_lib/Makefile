CC=gcc

build-example-lib:
	cd implementation_lib && \
	$(CC) -c -Wall -Werror -I"../" -fpic matelib.c && \
	$(CC) -shared matelib.o -o libmate.so && \
	rm matelib.o

build-example: build-example-lib
	cd use_lib && \
	$(CC) -g3 -Wall -L"../implementation_lib" -I"../" main.c -lmate -o example

run: build-example
	cd use_lib && \
	LD_LIBRARY_PATH="../implementation_lib/" ./example

clean:
	rm implementation_lib/libmate.so use_lib/example