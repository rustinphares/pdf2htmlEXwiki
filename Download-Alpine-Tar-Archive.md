## Download

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [Alpine](https://www.alpinelinux.org/) [Tar Archives](https://en.wikipedia.org/wiki/Tar_%28computing%29) built on a recent Alpine releases.

These Alpine tar archives come as two parts:
1. The tar archive itself which contains a `pdf2htmlEX` executable compiled inside an Alpine docker image (and hence using `musl`).
2. A `/bin/sh` script which will install the `pdf2htmlEX` Alpine dependencies using the `apk` command, and then unpacks the associated tar archive into the `/usr/local/bin` directory.

This option should only be chosen by someone who is comfortable using shell scripts in an Alpine Linux environment.

However, it *can* be used to build your own customized Alpine based docker image.

**NOTE:** at the moment, the statically linked FontForge and Poppler libraries are using the standard Alpine version of `iconv`. Unfortunately, the Alpine version of `iconv` is unable to deal with some 'standard' fonts, and so you *might* find these fonts are not transferred into the resulting html. See [Compile Alpine version of pdf2htmlEX using gnu-iconv](https://github.com/pdf2htmlEX/pdf2htmlEX/issues/63) for more details and discussion.