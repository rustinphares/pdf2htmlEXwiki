# Building for Fedora 21 

Install all dependencies (as seen here https://github.com/coolwanglu/pdf2htmlEX/wiki/Building) : 
``` bash
sudo yum install  cmake gcc gnu-getopt java-1.8.0-openjdk libpng-devel fontforge-devel cairo-devel poppler-devel libspiro-devel freetype-devel  poppler-data libjpeg-turbo-devel git
```

Clone the project : 
``` git clone https://github.com/coolwanglu/pdf2htmlEX.git ```

Configure build tools :
``` bash
cmake -DENABLE_SVG=ON --external-hint-tool=ttfautohint .
```

Build : 
```bash
make -j <your CPU core number>
```

Install :
``` bash
sudo make install
```

Note : The default build prefix is located at /usr/local/. So, make sure you have in your environement var named $PATH. To check if your are ok, execute : 
```bash 
echo $PATH | grep /usr/local/bin
```