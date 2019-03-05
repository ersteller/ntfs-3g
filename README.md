# Origins of this project 
This is forked from  
https://github.com/vitalif/ntfs-3g  

which is forked from this origin  
    git://ntfs-3g.git.sourceforge.net/gitroot/ntfs-3g/ntfs-3g  

# why?
well ... i deleted everything on my windows drive and i wanted to restore the user directory.
There was this tool **ntfsundelete** that restores single files or a bunch of them by nodeid. 
But *ntfsundelete* restores files in a single directory and i want it in the original directory structure and without name collisions of equal names. 
Also i wanted to be able to specify the parent directory to recover all of its content recursively. 

# build ntfsprogs
to build only ntfsprogs follow these steps

    ./configure 
    make ntfsprogs

to list all recoverable files with a complete path use the -A argument

    ./ntfsundelete </dev/unmounted_ntfs_drive>  -A
    
search for the directory and remember inode number of the directory

    ./ntfsundelete </dev/unmounted_ntfs_drive> -A -r <directory_node_id>
    
this prints all found files and directories in the selected *directory_node_id* recursifly.


when you are happy with the directory to undelete use following arguments.

    ./ntfsundelete </dev/unmounted_ntfs_drive> -A -u -r <directory_node_id> -d </destination/base/path/>
    
**-A** specifies that each node lists all parent directories up too root  
**-r directory_node_id** specifies the nodeid of the directory of which all content ntfsundelet is trying to recover.  
**-u** is the the undelete mode of ntfsundelete ***use at your own risk***  
**-d** specifies the destination path where ntfsundelete creates the undeleted files  



