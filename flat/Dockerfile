
# ChipYard on CentOs 7
FROM centos:7 

# Install dependencies 
# Note the run-around to install, uninstall, and upgrade `git`. 
RUN yum groupinstall -y "Development tools" && \
	yum install -y curl && \
	yum install -y gmp-devel mpfr-devel libmpc-devel zlib-devel vim git java java-devel && \
	curl https://bintray.com/sbt/rpm/rpm | tee /etc/yum.repos.d/bintray-sbt-rpm.repo && \
	yum install -y sbt texinfo gengetopt && \
	yum install -y expat-devel libusb1-devel ncurses-devel cmake "perl(ExtUtils::MakeMaker)" && \
	yum install -y python36 patch diffstat texi2html texinfo subversion chrpath git wget && \
	yum install -y gtk3-devel && \
	yum install -y python36-pip python36-devel rsync libguestfs-tools makeinfo expat ctags && \
	yum install -y centos-release-scl && \
	yum install -y devtoolset-8-make && \
	yum install -y dtc && \
	yum remove  -y git* && \
	yum install -y https://repo.ius.io/ius-release-el7.rpm https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
	yum install -y git224-all

# Clone and Install ChipYard
RUN source scl_source enable devtoolset-8 && \
	git clone https://github.com/ucb-bar/chipyard.git  && \
	cd chipyard && \
	./scripts/init-submodules-no-riscv-tools.sh && \
	./scripts/build-toolchains.sh riscv-tools 

