FROM jimbly/steamrt-amd64

RUN apt-get update && apt-get install --force-yes -y --no-install-recommends \
  gcc-4.8 g++-4.8 \
  # clang-3.4 lldb-3.4 \
  # clang-3.6 lldb-3.6 \
  && \
  update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.6 50 && \
  update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 50 && \
  update-alternatives --install /usr/bin/cpp cpp-bin /usr/bin/cpp-4.6 50 && \
  \
  update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 100 && \
  update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 100 && \
  update-alternatives --install /usr/bin/cpp cpp-bin /usr/bin/cpp-4.8 100 && \
  \
  # update-alternatives --install /usr/bin/gcc gcc /usr/bin/clang-3.4 50 && \
  # update-alternatives --install /usr/bin/g++ g++ /usr/bin/clang++-3.4 50 && \
  # \
  # update-alternatives --install /usr/bin/gcc gcc /usr/bin/clang-3.6 50 && \
  # update-alternatives --install /usr/bin/g++ g++ /usr/bin/clang++-3.6 50   && \
  \
  update-alternatives --set gcc /usr/bin/gcc-4.8 && \
  update-alternatives --set g++ /usr/bin/g++-4.8 && \
  update-alternatives --set cpp-bin /usr/bin/cpp-4.8 && \
  rm -rf /var/lib/apt/lists/*
