BUILD ?= obj
FILES=$(filter-out symbol_bfd.c symbol_mach.c, $(wildcard *.c))
TARGETS=benchmark
OBJS+=$(FILES:.c=.o)
CFLAGS += -D_GNU_SOURCE -g3 -Wall -Wextra -std=gnu11 -O2
LDFLAGS += -flto -O2


.PHONY: all clean


obj = $(addprefix $(BUILD)/, $(OBJS))

all: benchmark

benchmark: $(obj)
	$(CC) $(obj) -o $@ $(LDFLAGS)

$(BUILD)/%.o: %.c
	mkdir -p $(dir $@)
	$(CC) -c $< -o $@ $(CFLAGS)

clean:
	rm -rf ${BUILD} benchmark