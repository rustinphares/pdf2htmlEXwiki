## Download and Run

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [Docker](https://www.docker.com/) [images](https://docs.docker.com/engine/reference/commandline/image/) built on a range of recent Ubuntu and [Alpine](https://www.alpinelinux.org/) releases.

A Docker Image is a completely self contained collection of an executable (such as `pdf2htmlEX`) and all required shared libraries that it depends upon.

This means that a Docker image *should* be able to be run on distributions in which you can [install docker itself](https://docs.docker.com/get-docker/).

1. Pull an image from our [Docker Hub repository](https://hub.docker.com/r/pdf2htmlex/pdf2htmlex). 
2. Run it...

Runing `pdf2htmlEX` from a Docker image is the easiest way to convert a pdf file into html. With this option, you don't need knowledge on how to compile and install `pdf2htmlEX`.

## How to use this docker container to convert pdf file to html

Suppose you have a PDF file ~/pdf/test.pdf, simply running

    docker run -ti --rm -v ~/pdf:/root pdf2htmlex/pdf2htmlex pdf2htmlEX --zoom 1.3 test.pdf

would produce a single HTML file `test.html` in `~/pdf` directory.

## Run the docker container as local command

    alias pdf2htmlEX='docker run -ti --rm -v `pwd`:/root pdf2htmlex/pdf2htmlex pdf2htmlEX'
    pdf2htmlEX -h
    pdf2htmlEX --zoom 1.3 test.pdf

For detail on how to install docker, please refer to https://docs.docker.com/installation/

For detail on how to run pdf2htmlEX, please read the wiki https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Quick-Start

---

**NOTE:** The **Alpine docker image**, at the moment, statically links the FontForge and Poppler libraries using the standard Alpine version of `iconv`. Unfortunately, the Alpine version of `iconv` is unable to deal with some 'standard' fonts, and so you *might* find these fonts are not transferred into the resulting html. See [Compile Alpine version of pdf2htmlEX using gnu-iconv](https://github.com/pdf2htmlEX/pdf2htmlEX/issues/63) for more details and discussion.