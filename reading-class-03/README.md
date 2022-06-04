# Reading and Writing Files in Python

Files are named locations on disk to store related information. They are used to permanently store data in a non-volatile memory (e.g. hard disk).

Since Random Access Memory (RAM) is volatile (which loses its data when the computer is turned off), we use files for future use of the data by permanently storing them.

When we want to read from or write to a file, we need to open it first. When we are done, it needs to be closed so that the resources that are tied with the file are freed.

Hence, in Python, a file operation takes place in the following order:

1- Open a file 
2- Read or write (perform operation) 
3- Close the file  

## Files Open
Python has a built-in open() function to open a file. This function returns a file object, also called a handle, as it is used to read or modify the file accordingly.

>>> f = open("test.txt")    # open file in current directory
>>> f = open("C:/Python38/README.txt")  # specifying full path
## Files Close
Closing Files in Python
When we are done with performing operations on the file, we need to properly close the file.

Closing a file will free up the resources that were tied with the file. It is done using the close() method available in Python.

Python has a garbage collector to clean up unreferenced objects but we must not rely on it to close the file.

>>>f = open("test.txt", encoding = 'utf-8')
 >>>perform file operations
>>>f.close()



| Method |	Description |
| ----------- | ----------- |
close()	| Closes an opened file. It has no effect if the file is already closed.
detach() |	Separates the underlying binary buffer from the TextIOBase and returns it.
fileno() |	Returns an integer number (file descriptor) of the file.
flush() |	Flushes the write buffer of the file stream.
isatty() |	Returns True if the file stream is interactive.
read(n)	| Reads at most n characters from the file. Reads till end of file if it is negative or None.
readable() |	Returns True if the file stream can be read from.
readline(n=-1) |	Reads and returns one line from the file. Reads in at most n bytes if specified.
readlines(n=-1) |	Reads and returns a list of lines from the file. Reads in at most n bytes/characters if specified.
seek(offset,from=SEEK_SET) |	Changes the file position to offset bytes, in reference to from (start, current, end).
seekable() |	Returns True if the file stream supports random access.
tell() |	Returns an integer that represents the current position of the file's object.
truncate(size=None) |	Resizes the file stream to size bytes. If size is not specified, resizes to current location.
writable() |	Returns True if the file stream can be written to.
write(s) |	Writes the string s to the file and returns the number of characters written.
writelines(lines) |	Writes a list of lines to the file.

# Python Exceptions
This type of error occurs whenever syntactically correct Python code results in an error. The last line of the message indicated what type of exception error you ran into.
Python has many built-in exceptions that are raised when your program encounters an error (something in the program goes wrong).

When these exceptions occur, the Python interpreter stops the current process and passes it to the calling process until it is handled. If not handled, the program will crash.

For example, let us consider a program where we have a function A that calls function B, which in turn calls function C. If an exception occurs in function C but is not handled in C, the exception passes to B and then to A.

If never handled, an error message is displayed and our program comes to a sudden unexpected halt.

