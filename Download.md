pdf2htmlEX is available through several repositories, thanks to all the packagers!

 * [ArchLinux AUR](https://aur.archlinux.org/packages.php?ID=62426) by Arthur Titeica <arthur.titeica@gmail.com>
 * [Gentoo Overlay](http://gpo.zugaina.org/app-text/pdf2htmlex), gentoo-zh, mrueg or sunrise, by respective packagers. 
 * [Homebrew Formula](https://github.com/mxcl/homebrew/blob/master/Library/Formula/pdf2htmlex.rb) by Jamie Ly <me@jamie.ly>
 * [Macports](https://trac.macports.org/browser/trunk/dports/textproc/pdf2htmlex/Portfile) by Deepak Thukral <iapain@iapa.in>
 * [Windows win32 static](http://soft.rubypdf.com/software/pdf2htmlex-windows-verion) by Steven Lee <rubypdf@gmail.com>
 * [Docker image - 1.23GB](https://registry.hub.docker.com/u/klokoy/pdf2htmlex/) by Kim Lokøy <kim.lokoy@gmail.com>
 * [Docker image - 279MB](https://hub.docker.com/r/bwits/pdf2htmlex/) by Bill W <ozbillwang@gmail.com>
 * [Debian package](https://packages.debian.org/sid/pdf2htmlex) by josch <josch@mister-muffin.de>

Run from Docker container is the easiest way to convert pdf file to html, which you don't need knowledge on how to compile and install pdf2htmlEX.

## How to use this docker container to convert pdf file to html
Suppose you have a PDF file ~/pdf/test.pdf, simply running

    docker run -ti --rm -v ~/pdf:/pdf bwits/pdf2htmlex pdf2htmlEX --zoom 1.3 test.pdf

would produce a single HTML file `test.html` in `~/pdf` directory.

## Run the docker container as local command

    alias pdf2htmlEX="docker run -ti --rm -v ~/pdf:/pdf bwits/pdf2htmlex pdf2htmlEX"
    pdf2htmlEX -h 
    pdf2htmlEX --zoom 1.3 test.pdf

For detail on how to install docker, please refer to https://docs.docker.com/installation/

For detail on how to run pdf2htmlEX, please read the wiki https://github.com/coolwanglu/pdf2htmlEX/wiki/Quick-Start

The old Ubuntu PPA has been deprecated. We are looking for a maintainer.

You can also [build from source](https://github.com/coolwanglu/pdf2htmlEX/wiki/Building).