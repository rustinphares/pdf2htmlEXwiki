## Download, Install and Run

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [Debian Archives](https://en.wikipedia.org/wiki/Debian#Packages) built on a range of recent Ubuntu releases.

Our Debian archives (`*.deb`) *should* be able to be installed on [any distribution derived from Debian](https://en.wikipedia.org/wiki/Debian#Forks_and_derivatives), by using the `apt install` command.

Simply:
1. Download the `*.deb` file from our [releases page](https://github.com/pdf2htmlEX/pdf2htmlEX/releases).
2. Install it using the command `sudo apt install <<pathToDownloadedDebFile>>`.
3. Run it... (the executable is located in `/usr/local/bin` so make sure `/usr/local/bin` is in your PATH).

## Configuration

Our `*.deb` archives are *not* self contained, they required a number of additional packages to be  installed and properly configured.

The `apt install` command *should* install all required packages, however you may need to ensure these packages, such as, Fontconfig, and iconv are properly configured for *your* needs.

