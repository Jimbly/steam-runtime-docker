FROM jimbly/steamrt-precise-amd64-base

RUN apt-get update && apt-get install --force-yes -y --no-install-recommends \
  # skipping: ubuntu-minimal pkg-config time gdb
  build-essential \
  steamrt-dev \
  cmake \
  && rm -rf /var/lib/apt/lists/*
