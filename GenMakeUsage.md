# Introduction #

The usage info is also available via `gen_make.sh -h`.

# Requirements #

  * The script requires gcc, bash, ls, and mkdir.
  * For `make profile` target, gprof, [gprof2dot.py](http://code.google.com/p/jrfonseca/wiki/Gprof2Dot), and dot (graphwiz) are required.
  * For `make debug` target, gdb is required.
  * For automatic build number increment, awk is required.

# Details #

**Usage**:
> `gen_make.sh [options] exec`

The resulting Makefile is printed to **stdout**.
gen\_make currently supports building of executables, static libraries, and
shared libraries. This choice is done based on format of exec parameter.

  * **exec**
> > name of the output binary file to build

Options:
  * **-h**
  * **--help**
> > Prints this help message.
  * **-s**
> > Silent mode. On default, gen\_make script prints out some info about
> > selected configuration to **stderr**, this switch prevents this.
  * **-t** _target_
> > Build target. gen\_make supports targets **d, dp, r, rp**:
    * **'d'ebug**
    * **'d'ebug 'p'rofile**
    * **'r'elease** (default)
    * **'r'elease 'p'rofile**
> > For 'profile' targets, 'make profile' command is included, that creates profile.txt using gprof(1), and profile.png using [gprof2dot.py script](http://code.google.com/p/jrfonseca/wiki/Gprof2Dot) and dot.
  * **-f** '_flags_'
> > Additional flags to pass to compiler.
  * **-l** '_libs_'
> > Link libraries. Use **-l 'mylib urlib'** for '-lmylib -lurlib'.
  * **-c** _compiler_
> > Select compiler. Default is **g++**.
  * **-bn**
> > Enable build number. If selected, gen\_make will create BuildNum.h header file, if it does not exist yet, and will include script to automatically increment the build number on each build.
  * **-od** _dir\_name_
> > Output directory. gen\_make chooses name of output directory based on selected build target, and creates the directory. This switch allows you to select different directory.
  * **-exc** '_files_'
> > List of files excluded from build. E.g. **-exc 'file1.cpp file2.cpp'**.
  * **-par** '_parameters_'
> > Run parameters for the executable. gen\_make includes 'make run' and 'make debug' for executables, for executing and debugging using gdb(1), respectively. Here you can provide any parameters to the executable.
  * **-post** '_command_'
> > Provide any command that should be executed as a post-build step.
> > E.g. **-post 'echo We are done...'** (single quotes).
> > Command itself is not echo-ed by the make.