## By default Mac OSX comes with clang C++ compiler. This procedure installs and setup gcc C++ compiler for OSX so that you can use the VS Code IDE, etc, to write C++ on a Mac.

1.  brew install gcc

2. test 'g++-8' command, if you get this error: "g++-8: fatal error: no input files
compilation terminated.", that's a good sign. Run 'g++-8 --verson', should print this: "Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE."

3. cd /usr/local/bin/, g++ compiler will have been installed in this directory.

4. run command 'ln -s g++-8 g++' to link g++ to g++8.  g++ is now recognized by MacOS as c++ compiler, log out of MacOS and then log back in.

5. run command 'g++ --version', you should see this: "++ (Homebrew GCC 8.2.0) 8.2.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions..."  Please note: As of this writing, the version is: 8.x, obviously in the future, this will change.

### These settings have worked for me in MacOS VS Code -> tasks.json:
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "debug",
            "type": "shell",
            "command": "",
            "args": [
                "g++",
                "-g",
                "${relativeFile}",
                "-o",
                "a.exe"
            ]
        },
        {
            "label": "Compile and run",
            "type": "shell",
            "command": "",
            "args": [
                "g++",
                "-g",
                "${relativeFile}",
                "-o",
                "${fileBasenameNoExtension}.out",
                "&&",
                "clear",
                "&&",
                "./${fileBasenameNoExtension}.out"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": {
                "owner": "cpp",
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}"
                ],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
    ]
}`
`
