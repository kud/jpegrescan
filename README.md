# JPEGrescan: losslessly shrink any JPEG file
JPEGrescan is a perl script that uses jpeg tools to optimise jpeg compression by micro-managing some of the compression math based on research into some of the most common parameters.

NB: [MozJPEG](https://github.com/mozilla/mozjpeg) has the same optimisation built-in and is faster, so we recommend using MozJPEG when possible.

## Usage
```$ jpegrescan in.jpg out.jpg```

### Arguments
* -s: Removes all Exif data and now all JFIF data as well.  A basic 18-byte JFIF segment is added in its place.
* -i: Allows optimisations that may be "incompatible" with some software.  Currently this means removing *all* JFIF data (saving 18 bytes) and allowing an encoding not supported by Opera before version 11.61.
* -t: Turns on multithreaded operation.  Usually, uses up to 4 threads.  Faster, but not four times faster than without _-t_.  So try _xargs -n1 -P_ to shrink a large number of jpegs at the same time.
* -a: Turns on arithmetic coding.  Note this is unsupported by most software.
* -v: Verbose output.
* -q: Suppress all output.

## Package Availability
JPEGrescan is known to be packaged in the following distributions:
* Arch's User Repository
* NixOS

## Issues
* No out.jpg.  Install the following:
  * Fedora: ```yum -y install perl-File-Slurp libjpeg-turbo-utils```
  * Debian: ```aptitude install -y libfile-slurp-perl libjpeg-turbo-progs```

## Thanks
First, thanks to **Loren Merritt** who created this script originally.  Also, thanks to the people on [devshed](https://www.devshed.com/) and [lyncd](https://lyncd.com/) - whose names seem to be lost to the sands of time - who came up with the jfifremove idea and the basic C code.
