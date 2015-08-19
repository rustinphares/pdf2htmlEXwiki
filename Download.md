pdf2htmlEX is available through several repositories, thanks to all the packagers!

 * [ArchLinux AUR](https://aur.archlinux.org/packages.php?ID=62426) by Arthur Titeica <arthur.titeica@gmail.com>
 * [Gentoo Overlay](http://gpo.zugaina.org/app-text/pdf2htmlex), gentoo-zh, mrueg or sunrise, by respective packagers. 
 * [Homebrew Formula](https://github.com/mxcl/homebrew/blob/master/Library/Formula/pdf2htmlex.rb) by Jamie Ly <me@jamie.ly>
 * [Macports](https://trac.macports.org/browser/trunk/dports/textproc/pdf2htmlex/Portfile) by Deepak Thukral <iapain@iapa.in>
 * [Windows win32 static](http://soft.rubypdf.com/software/pdf2htmlex-windows-verion) by Steven Lee <rubypdf@gmail.com>
 * [Docker image - 1GB](https://registry.hub.docker.com/u/klokoy/pdf2htmlex/) by Kim Lokøy <kim.lokoy@gmail.com>
 * [Docker image - 279MB](https://hub.docker.com/r/bwits/pdf2htmlex/) by Bill W <ozbillwang@gmail.com>
   
   #### test pdf2htmlEX directly with below command, if you have docker installed
   docker run -ti --rm -v ~/pdf:/pdf bwits/pdf2htmlex pdf2htmlEX --zoom 1.3 /pdf/test.pdf /pdf/test.html

 * [Debian package](https://packages.debian.org/sid/pdf2htmlex) by josch <josch@mister-muffin.de>

The old Ubuntu PPA has been deprecated. We are looking for a maintainer.

You can also [build from source](https://github.com/coolwanglu/pdf2htmlEX/wiki/Building).