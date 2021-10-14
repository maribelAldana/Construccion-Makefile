PROCESS_NAME=build
IDIR =../include
#SHARED_IDIR = ../shared/include
CC=gcc
CFLAGS=-I$(IDIR)

ODIR=./obj
SRCDIR =./src
LIBS=-lcommons -lpthread -lreadline -lcunit -lrt

#SHARED_SRCDIR = ../shared/src
#SHARED_ODIR = ../shared/obj

DEPS = $(wildcard $(IDIR)/*.h)

SRC = $(wildcard $(SRCDIR)/*.c)
OBJ = $(patsubst $(SRCDIR)/%.c,$(ODIR)/%.o,$(SRC))

#$(ODIR)/%.o: $(SRCDIR)/%.c $(DEPS)
#	$(CC) -c -o $@ $< $(CFLAGS)

#$(SHARED_ODIR)/%.o: $(SHARED_SRCDIR)/%.c $(SHARED_DEPS)
#	$(CC) -c -o $@ $< $(CFLAGS)

#SHARED_DEPS = $(wildcard $(SHARED_IDIR)/*.h)

#SHARED_SRC = $(wildcard $(SHARED_SRCDIR)/*.c)
#SHARED_OBJ = $(patsubst $(SHARED_SRCDIR)/%.c,$(SHARED_ODIR)/%.o,$(SHARED_SRC))

$(PROCESS_NAME):
	cd $(SRCDIR) && \
	$(CC) -c -Wall -Werror $(CFLAGS) -fpic calculadora.c && \
	$(CC) -shared ../obj/calculadora.o -o ../obj/calculadora.so && \
	rm -f ./*.o

#ar rcs $(IDIR)/libcalculadora.a $(ODIR)/*.o

.PHONY: clean

clean:
	rm -f $(ODIR)/*.o *~ core $(INCDIR)/*~ $(PROCESS_NAME) 