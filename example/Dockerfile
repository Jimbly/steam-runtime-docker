FROM jimbly/steamrt-i386-gcc

# Additional packages I need for my build chain
RUN apt-get update && apt-get install -y --no-install-recommends \
  elfutils \
  && rm -rf /var/lib/apt/lists/*

# If anyone actually uses this, feel free to ping me for a more complete example
# including skeleton CMake project, build output parsing (so Visual Studio
# jumps to the right file/line), automatic mounting of the right directory,
# debug symbol generation/stripping/symstoring, symbol file uploads to a
# breakpad server, etc.
