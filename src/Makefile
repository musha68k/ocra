SRCS = lzma/lzmadec.c
OBJS = $(SRCS:.c=.o) stubicon.o
CC = gcc

CFLAGS = -Wall -O2 -DWITH_LZMA -Ilzma -s
# CFLAGS += -D_DEBUG
STUB_CFLAGS = -D_CONSOLE $(CFLAGS)
STUBW_CFLAGS = -mwindows $(CFLAGS)
# -D_MBCS

all: stub.exe stubw.exe edicon.exe

stubicon.o: stub.rc
	windres -i $< -o $@

stub.exe: $(OBJS) stub.o
	$(CC) $(STUB_CFLAGS) $(OBJS) stub.o -o stub

stubw.exe: $(OBJS) stubw.o
	$(CC) $(STUBW_CFLAGS) $(OBJS) stubw.o -o stubw

stub.o: stub.c
	$(CC) $(STUB_CFLAGS) -o $@ -c $<

stubw.o: stub.c
	$(CC) $(STUBW_CFLAGS) -o $@ -c $<

clean:
	rm -f $(OBJS) stub.exe stubw.exe edicon.exe edicon.o stubw.o stub.o

edicon.exe: edicon.o
	$(CC) $(CFLAGS) edicon.o -o edicon

