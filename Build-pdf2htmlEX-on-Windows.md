````````
========================
1. 安装msys2-i686-20160205.exe，目标目录F:\msys32。
2. 修改F:\msys32\etc\pacman.d，配置msys2和mingw-w64镜像(一般用户请忽略本步骤)。
3. 升级基本环境。
   运行msys2_shell.bat
   
   更新本地包数据    
   pacman -Sy
    
   升级核心包
   pacman -S --needed filesystem msys2-runtime bash libreadline libiconv libarchive libgpgme libcurl pacman ncurses libintl
   之后需要关闭所有 MSYS2 shell，然后运行 autorebase.bat（这个是必须的，不能省略）
    
   =============确认重新运行msys2_shell.bat=============
   升级其他包
   pacman -Su
   如果后面提示关闭，则重新运行msys2_shell.bat，再次执行一次命令。
4. 安装编译环境。
   pacman -S base-devel
   pacman -S mingw-w64-i686-toolchain
5. 确认编译环境。
   关闭msys2_shell.bat，执行autorebase.bat，然后执行mingw32_shell.bat。
   gcc -v确认能看到gcc 5.3.0。

6. 安装相关lib包，这里可以检查pdf2html编译文档，看看需要哪些程序库。
   这里可以用pacman -Sl查看软件列表，对比程序库名称。
   pacman -S wget mingw-w64-i686-curl mingw-w64-i686-zlib mingw-w64-i686-libffi mingw-w64-i686-pkg-config  mingw-w64-i686-gettext
   pacman -S mingw-w64-i686-glib2 mingw-w64-i686-libpng mingw-w64-i686-libjpeg-turbo mingw-w64-i686-xz mingw-w64-i686-libtiff mingw-w64-i686-lcms2
   pacman -S mingw-w64-i686-libjpeg-turbo mingw-w64-i686-openjpeg mingw-w64-i686-freetype mingw-w64-i686-libxml2 mingw-w64-i686-fontconfig mingw-w64-i686-pixman
   pacman -S mingw-w64-i686-cairo  mingw-w64-i686-openssl mingw-w64-i686-libssh2 mingw-w64-i686-poppler mingw-w64-i686-poppler-data mingw-w64-i686-pango 
   pacman -S mingw-w64-i686-libtool mingw-w64-i686-cmake git
   pacman -S mingw-w64-i686-nspr mingw-w64-i686-nss

   
==========正式编译================
1. 将需要编译的软件放在F:\msys32\home\用户名，解压得到fontforge-20160404和pdf2htmlEX-0.14.6。
2. 编译fontforge-20160404.tar.gz。
   cd fontforge-20160404
   ./bootstrap --force（运行成功，建议备份该目录，每次联网下载非常慢）
   ./configure --prefix=/mingw32 --disable-python-extension --disable-python-scripting && make && make install
3. 编译pdf2htmlEX-0.14.6.tar.gz
   先修改一下CMakeLists.txt
   先找到代码set(PDF2HTMLEX_LIBS ${PDF2HTMLEX_LIBS} ${FONTFORGE_LIBRARIES})
   在它之后添加
   # Add additional dependencies 
   set(PDF2HTMLEX_LIBS ${PDF2HTMLEX_LIBS} intl iconv gettextlib gettextpo gutils png jpeg openjpeg glib-2.0 z xml2 tiff gio-2.0 ltdl)
  
  修改CMakeLists.txt成功之后再执行编译命令。
  cd pdf2htmlEX-0.14.6
  mkdir build
  cd build
  cmake .. -G "MSYS Makefiles" -DCMAKE_INSTALL_PREFIX=/mingw32 -DENABLE_SVG=ON
  make && make install
==========验证和制作================
  mingw下的data目录不一样，编译后无法直接运行，会报“Error: Cannot open the manifest file”。

  解决方法：将/mingw32/share/pdf2htmlEX/*.*复制到pdf2htmlEX.exe相同目录的data子目录。pdf2htmlEX代码不用改，里面已经处理过data和tmp目录。
  
  将/mingw32/bin的全部*.dll和pdf2htmlEX.exe，以及data一起组成安装包。
````````