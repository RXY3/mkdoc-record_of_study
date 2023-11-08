# shell——key to the system
## overview of shell and some background knowledge
GUI 图形化  
> 1973 XeroxPARC Xerox Palo Alto  
> 1984 Apple Macintosh（Apple Lisa）
> 1985 Microsoft Windows（too much history——导致在目前其包袱过重，不利于开发）

shell 是在terminal内部允许的一种程序，它是用户与操作系统之间的接口。
### basic commands
- `ls` list
- `cd` change directory
> `cd ..` go back to the parent directory
> `cd ~` go back to the home directory
> `cd -` go back to the previous directory
> `cd /` go back to the root directory
> `cd .` go back to the current directory
- `pwd` print working directory
> `pwd -P` print the physical directory, without any symbolic links
> `pwd -L` print the logical directory, with symbolic links
> `pwd -W` print the windows directory, with windows format
> `pwd -h` print the help information
- `mkdir` make directory
- `rmdir` remove directory
  > `rmdir -p` remove the parent directory
- `touch` create a file
> `touch -a` change the access time
> `touch -m` change the modification time
> `touch -c` do not create any file
> `touch -r` use the reference file's time
> `touch -t` use the specified time
> `touch -h` change the symbolic link's time
- `rm` remove a file
> `rm -f` force to remove
> `rm -i` interactive mode
> `rm -r` remove a directory
> `rm -d` remove an empty directory
- `cp` copy a file
> `cp -f` force to copy
> `cp -i` interactive mode
> `cp -r` copy a directory
> `cp -d` copy a symbolic link
- `find [path] -name [filename]` find a file
> `find [path] -name [filename] -type [type]` find a file with a specific type
> `find [path] -name [filename] -type [type] -size [size]` find a file with a specific type and size
> `find [path] -name [filename] -type [type] -size [size] -exec [command]` find a file with a specific type and size, and execute a command
- pipe 
> `|` pipe
> > `ls -l | more` list all the files in the current directory, and show them page by page
> > `ls -l | grep [filename]` list all the files in the current directory, and find the file with the specific name
> > `ls -l | grep [filename] | more` list all the files in the current directory, find the file with the specific name, and show them page by page
> > `ls -l | grep [filename] | grep [filename]` list all the files in the current directory, find the file with the specific name, and find the file with the specific name
> `>` redirect
> > `ls -l > [filename]` list all the files in the current directory, and save them to a file
> > `ls -l | grep [filename] > [filename]` list all the files in the current directory, find the file with the specific name, and save them to a file
> > `ls -l | grep [filename] | grep [filename] > [filename]` list all the files in the current directory, find the file with the specific name, and find the file with the specific name, and save them to a file
## shell script
TODO






