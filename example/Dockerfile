FROM jimbly/steamrt-i386-gcc

# Additional packages I need for my build chain
RUN apt-get update && apt-get install -y --no-install-recommends \
  elfutils \
  && rm -rf /var/lib/apt/lists/*
