# Handling the Gperf code
GPERF = /usr/bin/gperf
# everything should be inside ../common/scpi-const.gperf../common/scpi-const.gperf
GPERFFLAGS = 
BUILT_SOURCES = ../commom/scpi-const.c

PROG = test

SRCS = main.c ../common/scpi-def.c

CFLAGS += -Wextra -Wmissing-prototypes -Wimplicit -I ../../libscpi/inc/
LDFLAGS += -lm ../../libscpi/dist/libscpi.a -Wl,--as-needed

.PHONY: clean all

all: $(PROG)

OBJS = $(SRCS:.c=.o)

.c.o:
	$(CC) -c $(CFLAGS) $(CPPFLAGS) -o $@ $<

../common/scpi-def.c: ../common/scpi-const.c
../common/scpi-const.c: ../common/scpi-const.gperf
	$(GPERF) $(GPERFFLAGS) < $< > $@ 

$(PROG): $(OBJS)
	$(CC) -o $@ $(OBJS) $(CFLAGS) $(LDFLAGS)

clean:
	$(RM) $(PROG) $(OBJS)
