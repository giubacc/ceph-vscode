FROM opensuse/leap:15.4

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Add OBS repository for additional dependencies necessary on Leap 15.4
RUN zypper ar \
  https://download.opensuse.org/repositories/filesystems:/ceph:/s3gw/15.4/ \
  s3gw-deps \
 && zypper --gpg-auto-import-keys ref
RUN zypper -n install --no-recommends \
      'cmake>3.5' \
      'fmt-devel>=6.2.1' \
      'gperftools-devel>=2.4' \
      'libblkid-devel>=2.17' \
      'liblz4-devel>=1.7' \
      'libthrift-devel>=0.13.0' \
      'pkgconfig(libudev)' \
      'pkgconfig(systemd)' \
      'pkgconfig(udev)' \
      babeltrace-devel \
      binutils \
      ccache \
      cmake \
      cpp11 \
      cryptsetup-devel \
      cunit-devel \
      fdupes \
      fuse-devel \
      gcc-c++ \
      gcc11 \
      gcc11-c++ \
      git \
      gperf \
      jq \
      keyutils-devel \
      libaio-devel \
      libasan6 \
      libboost_atomic1_80_0-devel \
      libboost_context1_80_0-devel \
      libboost_coroutine1_80_0-devel \
      libboost_filesystem1_80_0-devel \
      libboost_iostreams1_80_0-devel \
      libboost_program_options1_80_0-devel \
      libboost_python-py3-1_80_0-devel \
      libboost_random1_80_0-devel \
      libboost_regex1_80_0-devel \
      libboost_system1_80_0-devel \
      libboost_thread1_80_0-devel \
      libbz2-devel \
      libcap-ng-devel \
      libcap-devel \
      libcurl-devel \
      libexpat-devel \
      libicu-devel \
      libnl3-devel \
      liboath-devel \
      libopenssl-devel \
      libpmem-devel \
      libpmemobj-devel \
      librabbitmq-devel \
      librdkafka-devel \
      libsqliteorm \
      libstdc++6-devel-gcc11 \
      libtool \
      libtsan0 \
      libxml2-devel \
      lttng-ust-devel \
      lua-devel \
      lua53-luarocks \
      make \
      memory-constraints \
      mozilla-nss-devel \
      nasm \
      ncurses-devel \
      net-tools \
      ninja \
      ninja \
      openldap2-devel \
      patch \
      perl \
      pkgconfig \
      procps \
      python3 \
      python3-Cython \
      python3-PrettyTable \
      python3-PyYAML \
      python3-Sphinx \
      python3-devel \
      python3-setuptools \
      rdma-core-devel \
      re2-devel \
      rpm-build \
      snappy-devel \
      sqlite-devel \
      systemd-rpm-macros \
      systemd-rpm-macros \
      valgrind-devel \
      xfsprogs-devel \
      xmlstarlet \
      sudo \
      gdb \
      bash-completion \
      curl \
      docker \
      docker-compose \
      vi \
 && zypper clean --all

# Create the user
ADD puthnfo.sh /usr/bin/
ADD hnfo /
RUN puthnfo.sh

ADD bashrc.patch /
RUN /bin/bash -c "cat /bashrc.patch >> /home/$USERNAME/.bashrc"

USER $USERNAME
