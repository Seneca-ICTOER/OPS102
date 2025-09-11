# Access Control Lists 

Windows and Linux both offer File Access Control Lists (FACLs or ACLs)
to provide fine-grained control of file access. ACLs allow individual
file permissions to be granted or denied to individual users and groups.
However, the management of ACLs can be a complicated subject, and even
experienced users sometimes misconfigure ACLs!

Due to this complexity, we will not be covering ACLs in this
introductory course.

However, on a Windows system, basic manipulation of ACLs can be
performed using the Windows Explorer file manager. Select a file which
is stored on an NTFS filesystem (most internal hard disks or solid state
disks, but not external drives) and right-click on it to view the
file\'s Properties. Select the Security tab on the dialog that is
displayed to view the users for which ACLs have been created, and the
basic permissions that have been allowed or denied for that user on the
selected file. Note that the effective permission will be a combination
of the permissions allowed/denied on the file as well as on the parent
directories.