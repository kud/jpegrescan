# JPEGrescan: losslessly shrink any JPEG file 

JPEGrescan is a perl script that uses jpeg tools to optimize jpeg compression by micro-managing some of the compression math based on research into some of the most common parameters.

## Usage

```$ jpegrescan in.jpg out.jpg ```

### Arguments

* -s: Removes all Exif data and now all JFIF data as well.  (A basic 18-byte JFIF segment is added in its place.)
* -i: Allows optimizations that may be "incompatible" with some software.  Currently this means removing *all* JFIF data (saving 18 bytes) and allowing an encoding not supported by Opera before version 11.61.
* -t: Turns on multithreaded operation.  Usually, uses up to 4 threads.  Faster, but not four times faster than without -t.  So try xargs -n1 -P to shrink a large number of jpegs at the same time.
* -a: Turns on arithmetic coding. (Unsupported by most software.)  
* -v: verbose output
* -q: supress all output

##Issues 
* No out.jpg - Install the below packages to solve this issue
  yum -y install perl-File-Slurp libjpeg-turbo-utils 

## Thanks

First, thanks to **Loren Merritt** who created this script originally.  Also, thanks to the people on devshed.com and lyncd.com - whose names seem to be lost to the sands of time - who came up with the jfifremove idea and basic C code.
