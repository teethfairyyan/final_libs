-include ../common/Makefile.common

TARGET = test

INC = -I$(INSTALL_PATH)/$(INCLUDE_PATH)
LL = -L$(INSTALL_PATH)/$(LIBS_PATH)
LIBS = -lfhash \
	   -lfmempool \
	   -lpthread \
	   -lflock \
	   -lflog \
	   -lfmbuf \
	   -lftimer \
	   -lrt \
	   -lflist \
	   -lfev \
	   -lfnet \
	   -lfcache \
	   -lfco \
	   -lftu

SRCS = main.c \
	   t_hash.c \
	   t_mem.c \
	   t_log.c \
	   t_mbuf.c \
	   t_timer.c \
	   t_list.c \
	   t_fev.c \
	   t_fcache.c \
	   t_fco.c

COPY_FILES = 
	   
DEPS = $(patsubst %.c,%.d,$(SRCS))
OBJS = $(patsubst %.c,%.o,$(SRCS))

CFLAGS += $(EXT_FLAGS)
CFLAGS +=

all:$(TARGET)
$(TARGET):$(OBJS) $(DEPS)
	$(CC) $(CFLAGS) $(EXT_FLAGS) $(INC) $(LL) -o $(TARGET) $(OBJS) $(LIBS)

%.d:%.c
	$(CC) $(INC) -MM $< > $@
%.o:%.c 
	$(CC) $(CFLAGS) $(INC) -c $< 

run_test:
	./$(TARGET)

.PHONY:clean
clean:
	rm -f $(DEPS) $(OBJS) $(TARGET)
	rm -f test_async_log*
	rm -f test_log*

help:
	@echo "The information represents in the program:"
	@echo "Final executable name: $(TARGET)"
	@echo "Source files: $(SRCS)"
	@echo "Object files: $(OBJS)"
depend:$(DEPS)
	@echo "Dependencies are now up-to-date"
-include $(DEPS)
