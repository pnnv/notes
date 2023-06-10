Related: [[Filesystems & Drive Layout]]

----
Metadata is the information about a file, rather than the data contained in the file. Most file formats have room for metadata towards the front of the file, which means the metadata for the file is stored inside of the file, but not considered to be the part of the file itself. It is possible to remove the metadata of the file without effecting the way the file displays.

To pull the metadata from a file, use a tool for it, like this one: [http://exif.regex.info/exif.cgi](http://exif.regex.info/exif.cgi)

Another type of metadata is the filesystem metadata. Rather than being included in the file itself, it is stored in the inode table. Use `ls -i` to get the inode information for a file and then use `debugfs -R "stat` to get all the information for the file, including the filesystem metadata.

A third type of metadata is information about who sends and receives information. Even if the content can't be decrypted, just knowing who sends to who is useful information and can be dangerous depending on the context.