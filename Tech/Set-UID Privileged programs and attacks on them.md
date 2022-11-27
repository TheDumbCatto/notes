***
## 1. The risks faced by [Set-UID programs](Set-UID%20programs.md)

### User inputs
If not properly sanitized, user inputs can cause a Set-UID program to run arbitrary tasks additionally to the ones it is assigned.
>A famous example is the change-shell program *chsh* which writes to the file */etc/passwd* to change the default [shell](Shell.md) of the user. User input was not properly controlled and that allowed the user to provide two lines of text as the input, thus made it possible for attackers to create a new account on the system.

### System inputs
If a privileged program uses system inputs and those inputs are controllable by normal users, attackers can consequently control the input of that privileged program.
>For example, if a program is fixed to make changes to file */tmp/xyz*, an attacker can create a [symbolic link](Symbolic%20link.md) to make */tmp/xyz* point to */etc/shadow* and as a result they can make changes to */etc/shadow* through the program.

### Capability leaking
If a privileged program gains privileged capabilities and forgets to clean those capabilities when the privilege is downgraded, that unwiped capability can be accessible by non-privileged processes.
> An example would be the use of [file descriptor](File%20descriptor.md). If, let's say, a privileged C program is written to edit a privileged file and notify the user of the file descriptor in use, but forget to close the file after all tasks are finished, an attacker can utilize that file descriptor and make changes to the privileged file even if he has no privileges at all. 


### Hidden inputs (Env variables)
If used as inputs, environment variables can potentially be utilized by attackers to affect the behavior of a program.
> For example, if a privileged C program runs *system("ls")* to list the files of a directory on the host, an attacker can utilize the fact that no full path to *ls* was given in the argument, and modify the ***PATH*** env variable by adding the path to a malicious ls program that he created himself, so that the unsafe program would invoke that malicious program first.


***
## 2. Lessons learned
Follow the [Principle of least privilege](Security%20principles.md#Principle%20of%20least%20privilege)
and the [Principle of data/code isolation](Security%20principles.md#Principle%20of%20data/code%20isolation)