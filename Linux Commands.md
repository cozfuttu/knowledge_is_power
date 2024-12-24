### Navigation
`cd <directory>`: Change Directory, for moving around the filesystem (ex `cd /home`, or `cd ..` for going back one level)
`pwd`: Print Working Directory, shows your current dirrectory.
`ls`: List, lists the contents of your directory (ex. `ls` or `ls /home` or `ls -l`)

### User
`su`: Switch User, for switching the active user (use `su -` for becoming root)
`clear`: Clears terminal
`whoami`: Shows Active user
`passwd`: Chaning Password of the active user

### Creating Files & Directories
`touch <file>`: Creates an empty file
`cp <sourceFile> <targetFile>` : Copies file (`cp -R` for directories )
`vi <file>`: Creates an empty file and opens vi editor
`mkdir`: Creates a directory
`mv <sourceFile> <targetFile>`: Moves file.
`ln`: Creates a hard link (shortcut) (use `ln -s` for soft link).

### Finding Files & Directories
`find <startDirectory> -name <file>`: Finds where the specified file is.
`locate <file>`: Locates where the specified file is. Faster than `find`, but relies on its own local database, so might not work correctly. To update its database, run `updatedb`.

### Other
`man <command>`: Shows manual of the specified command