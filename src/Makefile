# src/Makefile

PROC = proc
CC = gcc

# Paths
INCLUDES = -I$(ORACLE_HOME)/precomp/public -I../include
LDFLAGS = -L$(ORACLE_HOME)/lib -lclntsh

PCFILES = main.pc db_ops.pc
CFILES = $(PCFILES:.pc=.c)
OBJS = $(CFILES:.c=.o)

TARGET_DIR = ../bin
TARGET = $(TARGET_DIR)/app

all: $(TARGET_DIR) $(TARGET)

$(TARGET_DIR):
	mkdir -p $(TARGET_DIR)

$(TARGET): $(OBJS)
	$(CC) -o $@ $(OBJS) $(LDFLAGS)

%.c: %.pc
	$(PROC) INCLUDE=../include $<

%.o: %.c
	$(CC) -c $< $(INCLUDES)

clean:
	rm -f *.o *.c $(TARGET)
