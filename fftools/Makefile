# Compiler and linker flags
CC ?= gcc
CFLAGS += -fPIC -Wall -Wextra
LDFLAGS += -shared

# FFmpeg library dependencies
FFMPEG_LIBS = -lavcodec -lavformat -lavfilter -lavdevice -lavutil -lswresample -lswscale

# Source files
FFMPEG_SRCS = fftools/ffmpeg.c \
              fftools/ffmpeg_dec.c \
              fftools/ffmpeg_demux.c \
              fftools/ffmpeg_enc.c \
              fftools/ffmpeg_filter.c \
              fftools/ffmpeg_hw.c \
              fftools/ffmpeg_mux.c \
              fftools/ffmpeg_mux_init.c \
              fftools/ffmpeg_opt.c \
              fftools/ffmpeg_sched.c \
              fftools/sync_queue.c \
              fftools/thread_queue.c \
              fftools/cmdutils.c \
              fftools/opt_common.c

# Object files
FFMPEG_OBJS = $(FFMPEG_SRCS:.c=.o)

# Main target
all: libffmpeg.so

# Build shared library
libffmpeg.so: $(FFMPEG_OBJS)
	$(CC) $(LDFLAGS) -o $@ $^ $(FFMPEG_LIBS)

# Build object files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# Clean target
clean:
	rm -f $(FFMPEG_OBJS) libffmpeg.so

.PHONY: all clean