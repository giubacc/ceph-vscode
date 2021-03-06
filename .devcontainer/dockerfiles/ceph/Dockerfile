FROM opensuse/tumbleweed

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN zypper -n install sudo dnf bash make git ccache cmake ninja gdb\
  jq binutils bash-completion curl docker docker-compose
RUN zypper -n install --no-recommends systemd-rpm-macros rpm-build
RUN zypper -n install --no-recommends \
  babeltrace-devel 'cmake>3.5' cryptsetup-devel cunit-devel fdupes \
  'fmt-devel>=6.2.1' fuse-devel gcc-c++ golang-github-prometheus-prometheus \
  gperf 'gperftools-devel>=2.4' keyutils-devel libaio-devel \
  'libblkid-devel>=2.17' libbz2-devel libcap-ng-devel libcurl-devel \
  libexpat-devel libicu-devel 'liblz4-devel>=1.7' libnl3-devel liboath-devel \
  libopenssl-devel libpmem-devel libpmemobj-devel 'libthrift-devel>=0.13.0' \
  libtool libxml2-devel lttng-ust-devel lua-devel lua54-luarocks make \
  memory-constraints mozilla-nss-devel nasm ncurses-devel net-tools ninja \
  openldap2-devel patch perl pkgconfig 'pkgconfig(libudev)' \
  'pkgconfig(systemd)' 'pkgconfig(udev)' procps python3 python3-Cython \
  python3-PrettyTable python3-PyYAML python3-Sphinx python3-devel \
  python3-setuptools rdma-core-devel re2-devel snappy-devel sqlite-devel \
  systemd-rpm-macros valgrind-devel which xfsprogs-devel xmlstarlet
# Use prebuilt boost
RUN zypper -n install --no-recommends \
      libboost_atomic1_79_0-devel \
      libboost_context1_79_0-devel \
      libboost_coroutine1_79_0-devel \
      libboost_filesystem1_79_0-devel \
      libboost_iostreams1_79_0-devel \
      libboost_program_options1_79_0-devel \
      libboost_python-py3-1_79_0-devel \
      libboost_random1_79_0-devel \
      libboost_regex1_79_0-devel \
      libboost_system1_79_0-devel \
      libboost_thread1_79_0-devel \
      librabbitmq-devel \
      librdkafka-devel \
 && zypper clean --all

# Create the user
ADD puthnfo.sh /usr/bin/
ADD hnfo /
RUN puthnfo.sh

ADD bashrc.patch /
RUN /bin/bash -c "cat /bashrc.patch >> /home/$USERNAME/.bashrc"

USER $USERNAME
