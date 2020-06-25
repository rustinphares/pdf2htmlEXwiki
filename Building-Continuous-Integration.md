We currently use two different Continuous Integration (CI) tools.

Firstly, [Travis-CI](https://travis-ci.org/github/pdf2htmlEX) compiles and checks every commit to pdf2htmlEX/pdf2htmlEX project. However, Travis only builds using Ubunut Bionic.

So, we also use the [Laminar](https://laminar.ohwg.net/) CI tool (locally) to build, test and release `pdf2htmlEX` on multiple Ubuntu releases, as well as Alpine Linux v3.12. Using the [stephengaito/laminar-scripts](https://github.com/stephengaito/laminar-scripts) and [stephengaito/pdf2htmlex-laminar-scripts](https://github.com/stephengaito/pdf2htmlex-laminar-scripts) projects, we build and test `pdf2htmlEX` inside a number of different [Docker](https://www.docker.com/) images. This allows us to more carefully control the exact collection of installed libraries, to ensure we *know* exactly which packages are needed to run `pdf2htmlEX`.

