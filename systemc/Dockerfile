FROM       rgly/coding-env
MAINTAINER Chia-Wei Chang "https://github.com/rgly"

RUN apt-get update \
    && apt-get install -y libncurses5-dev autoconf automake perl verilator \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# install systemc
RUN wget https://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.3.tar.gz \
    && tar -zxf systemc-2.3.3.tar.gz \
    && cd systemc-2.3.3 \
    && export CXX=g++-8 \
    && ./configure --prefix=/opt/systemc-2.3.3 \
    && make -j4 && make install \
    && cd .. \
    && rm -f systemc-2.3.3.tar.gz \
    && rm -rf systemc-2.3.3 

# install scml
RUN git clone https://gitlab.larc-nthu.net/rgly/scml.git \
    && export CXX=g++-8 \
    && mkdir scml/build \
    && mkdir /opt/scml \
    && cd scml \
    && sed -i -e 's/g++-5\.2\.0/g++-5\.2\.0 \| g++-8/g' ./configure.in \
    && sed -i -e '25s/^/#include \<sstream\>/' src/scml2_base/callback_observers_owner.h \
    && autoconf \
    && cd build \
    && ../configure --prefix=/opt/scml --with-systemc=/opt/systemc-2.3.3 \
    && make install -j4 \
    && cd ../.. \
    && rm -rf scml
