PROCESS_NAME=example_use
IDIR =../example_use_lib/include
IDIRLIB=../example_library/src
CC=gcc
CFLAGS=-g3 -Wall -L../example_library/src -I$(IDIR) 

ODIR=./obj
SRCDIR =./src
LIBS=-lcalculadora

DEPS = $(wildcard $(IDIR)/*.h)

SRC = $(wildcard $(SRCDIR)/*.c)
OBJ = $(patsubst $(SRCDIR)/%.c,$(ODIR)/%.o,$(SRC))

#$(ODIR)/%.o: $(SRCDIR)/%.c $(DEPS)
#	$(CC) -c -o $@ $< $(CFLAGS)

build:
	cd /example_library/src && \
	$(CC) -c -Wall -Werror -I../include -fpic calculadora.c && \
	$(CC) -shared ../calculadora.o -o ../obj/calculadora.so && \
	rm -f ./*.o


example_use: build
	cd ../example_use_lib && \
	$(CC) $(CFLAGS) ./src/example_use_lib.c -lcalculadora -o ./obj/example_use_lib


run: $(PROCESS_NAME)
	LD_LIBRARY_PATH=$(IDIRLIB) ./example_use_lib

.PHONY: build example_use run

