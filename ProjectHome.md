Bash script to generate Makefile based on C/C++ source code files in current directory, using `gcc -MM`.

Script contains support for:
  * executables, static libraries, and dynamic link libraries, based on the output file format,
  * automatic increment of build number on each build (the header file including the version and build number is automatically generated),
  * several build targets - debug, debug profile, release, release profile,
  * easily specifying additional flags passed to compiler,
  * passing list of link libraries used for build,
  * selectively excluding files from build, and more...