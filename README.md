# pdf2htmlex on Ubuntu 18.04 (Bionic Beaver)

0. apt-get install -y build-essential checkinstall git cmake

1. Install m4
wget ftp://ftp.gnu.org/gnu/m4/m4-1.4.18.tar.gz && tar -xvzf m4-*.tar.gz
cd m4-1.4.18 && ./configure --prefix=/usr/local/m4 && make -j4 && make install

2. Install popper
apt-get install -y  pkg-config libopenjp2-7-dev libopenjp2-7 libgdk-pixbuf2.0-dev libfontconfig1-dev libfontforge-dev poppler-data poppler-utils
wget https://poppler.freedesktop.org/poppler-0.63.0.tar.xz && tar -xvf poppler-0.63.0.tar.xz
cd poppler-0.63.0
cmake -DENABLE_XPDF_HEADERS=ON .
make -j 4 && make install

3. Install libcairo,libfontforge, libpango
apt install -y libcairo-dev libfontforge-dev libpango1.0-dev

4. pkg-config --print-provides --cflags --libs poppler

5. Clone and install the pdf2htmlEX git repo
git clone https://github.com/pdf2htmlEX/pdf2htmlEX.git
cd pdf2htmlEX
cmake . 
make -j4 && make install
