# Download and Run

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [Docker](https://www.docker.com/) [images](https://docs.docker.com/engine/reference/commandline/image/) built on a range of recent Ubuntu and [Alpine](https://www.alpinelinux.org/) releases.

A Docker Image is a completely self contained collection of an executable (such as `pdf2htmlEX`) and all required shared libraries that it depends upon.

This means that a Docker image *should* be able to be run on distributions in which you can [install docker itself](https://docs.docker.com/get-docker/).

1. Pull an image from our [Docker Hub repository](https://hub.docker.com/r/pdf2htmlex/pdf2htmlex). 
2. Run it...

Running `pdf2htmlEX` from a Docker image is the easiest way to convert a pdf file into html. With this option, you don't need knowledge on how to compile and install `pdf2htmlEX`.

### How to use this docker container to convert pdf file to html

Suppose you have a PDF file ~/pdf/test.pdf, simply running

    docker run -ti --rm -v ~/pdf:/pdf -w /pdf pdf2htmlex/pdf2htmlex --zoom 1.3 test.pdf

would produce a single HTML file `test.html` in your `~/pdf` directory.

### Run the docker container as local command

    alias pdf2htmlEX='docker run -ti --rm -v `pwd`:/pdf -w /pdf pdf2htmlex/pdf2htmlex'
    pdf2htmlEX -h
    pdf2htmlEX --zoom 1.3 test.pdf

For details on how to install docker, please refer to https://docs.docker.com/installation/

For details on how to run pdf2htmlEX, please read the wiki https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Quick-Start

# Docker mount points and using your own configuration

You can use the [`docker run` `-v` command line switch](https://docs.docker.com/engine/reference/commandline/run/#mount-volume--v---read-only) to mount directories on your local machine to directories *inside* the running `pdf2htmlEX` docker container. The `-v` switch takes one argument which consists of two paths separated by a single ':' character. The first path is the path to the directory on your *local* machine that you want mounted inside the running container. The second path is the path to the directory *inside* the running container which should contain the files from your computer.

You *must* use this to mount the directory containing your `pdf` files to a location inside the running docker container for `pdf2htmlEX` to access.
You can also use this to mount the directory where you want the resulting `html` output to be placed.

Finally, you can also use the `-v` switch to mount your own configuration files for `pdf2htmlEX` to use.

At the moment the `pdf2htmlEX` docker image uses the following directories:

1. The docker container's 'working directory' is `/pdf`. This means unless you use the [`docker run` `-w` command line switch](https://docs.docker.com/engine/reference/commandline/run/#set-working-directory--w), `pdf2htmlEX` expects all files to be located in the `/pdf` directory.

2. The `pdf2htmlEX` 'data directory' is `/usr/local/share/pdf2htmlEX`. This directory contains the `css`, `js`, and `manifest` files which are used to create the output `html`. Most users will not need to change these files, however you can use your own versions of these files by mounting your own directory over the `/usr/local/share/pdf2htmlEX` directory inside the docker container. (If you do this you *must* also mount your own copy of the 'poppler data'... see below).

3. The `pdf2htmlEX` '[poppler](https://poppler.freedesktop.org/) data directory' is `/usr/local/share/pdf2htmlEX/poppler`. This directory contains the ['poppler data'](https://poppler.freedesktop.org/poppler-data-0.4.9.tar.gz) required to configure the statically linked poppler library. In particular this 'poppler data' is required for the correct handling of CJK characters (among many others).

4. The `pdf2htmlEX` executable expects to find various font configuration files in the `/etc/fonts` directory. You can use your own configuration by mounting your copy over the container's `/etc/fonts` directory. *However, if you do this, then you many need to mount all other associated font directories as well* (you can use your package manager tool to identify where these associated directories and files are located).

---

**NOTE:** The **Alpine docker image**, at the moment, statically links the FontForge and Poppler libraries using the standard Alpine version of `iconv`. Unfortunately, the Alpine version of `iconv` is unable to deal with some 'standard' fonts, and so you *might* find these fonts are not transferred into the resulting html. See [Compile Alpine version of pdf2htmlEX using gnu-iconv](https://github.com/pdf2htmlEX/pdf2htmlEX/issues/63) for more details and discussion.