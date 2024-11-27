13/09/2024 0631

Status #idea

Tags:

# Linux file permissions

For aws, 
Connect to ec2 and launch/connect instance to the cli
move to location where the file you wish to change permissions is and then
ls -l
this will show more details of the file/directory
the first letter shown refer to the permissions given to owner/group/others
ie -rw-r--r--
first - indicates that its a text file id was a d that would mean its a directory
next are in groups of 3
rw- indicates the owner of the file can r (read), w (write) - (nothing)
r-- indicates the group can r (read), - (nothing), - (nothing)
final r-- indicates anyone else can r (read), - (nothing), - (nothing)

the following number is how many paths to the file, next is the name of the owner, then the size of the file in bytes, then date and time of when the file was last modified

Its important to set permissions to protect possible sensitive data from being accessed by anyone.

chmod+ adds permissions
chmod- removes permissions
these numbers are how to change the permissions
4 (read), 2 (write), 1 (execute)
to change permissions
chmod 644 file name/directory
the number is reach by adding the permissions needed together.
ie 6 = 4 (read)+2 (write)=6
first number is owner
second is group
third is everyone else

the make sure to shutdown the instance to avoid charges while training
close cli
go to the instance
instance state
terminate instance
# References
