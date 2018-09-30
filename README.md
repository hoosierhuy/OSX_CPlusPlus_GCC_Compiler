## By default Mac OSX comes with clang C++ compiler. This procedure installs and setup gcc C++ compiler for OSX so that you can use the VC Code IDE to write C++ on a Mac.

1.  brew install gcc

2. test 'g++-8' command, if you get this error: "g++-8: fatal error: no input files
compilation terminated.", that's a good sign. Run 'g++-8 --verson', should print this: "Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE."

3. cd /usr/local/bin/, g++ compiler will have been installed in this directory.

4. run command 'ln -s g++-8 g++' to link g++ to g++8.  g++ is now recognized by MacOS as c++ compiler, log out of MacOS and then log back in.

5. run command 'g++ --version', you should see this: "++ (Homebrew GCC 8.2.0) 8.2.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions..." 
