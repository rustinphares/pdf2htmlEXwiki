## Download, Install and Run

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [Debian Archives](https://en.wikipedia.org/wiki/Debian#Packages) built on a range of recent Ubuntu releases.

Our Debian archives (`*.deb`) *should* be able to be installed on [any distribution derived from Debian](https://en.wikipedia.org/wiki/Debian#Forks_and_derivatives), by using the `apt install` command.

Simply:
1. Download the `*.deb` file from our [releases page](https://github.com/pdf2htmlEX/pdf2htmlEX/releases).
2. Install it using the command `sudo apt install <<pathToDownloadedDebFile>>` (see note below).
3. Run it... (the executable is located in `/usr/local/bin` so make sure `/usr/local/bin` is in your PATH).

## Configuration

Our `*.deb` archives are *not* self contained, they required a number of additional packages to be  installed and properly configured.

The `apt install` command *should* install all required packages, however you may need to ensure these packages, such as, Fontconfig, and iconv are properly configured for *your* needs.

## Notes:

### Using apt install to install a *.deb file

Assuming you have downloaded one of the release `*.deb` files to your local directory and called it `pdf2htmlEX.deb` then the correct `apt install` command would be:

```
  sudo apt install ./pdf2htmlEX.deb
```

It is very important that you use a (relative or absolute) *path* to the `*.deb` file. It is the `./` in front of the `pdf2htmlEX.deb` file name which tells `apt install` that it is supposed to install a *local file* rather than a *package name* in `apt install`'s internal package database.

*Alternatively* you could use the following commands:

```
  sudo dpkg -i pdf2htmlEX.deb
  apt-get install -f
```
