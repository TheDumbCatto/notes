## How a process get its env variables

Basically there are 2 ways:
1. A process is created as a child process -> The child's memory is a duplicate of the parent's memory -> Inherits all env variables from the parent (see [Shell variables vs Environment variables](#Shell%20variables%20vs%20Environment%20variables) to see what exactly are passed down to child from shell parent)
2. A process is created as a replacement of the current process -> Inherits env variables that are passed through `execve()`

## Memory location for env variables

The location of env variables in a program's [stack](Stack%20memory.md) is depicted below
![](Env%20var%20location.jpg)

## Shell variables vs Environment variables
- All initial shell variables are copied from environment variables. When an user makes changes to shell variables (through `export` or `unset` or explicit assignment), environment variables aren't affected.
> Consider the following example. `environ` is a file stored in every process' directory and displays the environment of that process. `\$\$` is a special *bash variable* representing the PID of the current shell process. Therefore `/proc/\$\$/environ` will give the environment variables of the current shell process.
> ```
> $ strings /proc/\$$/environ | grep LOGNAME
> LOGNAME=seed
> $ echo $LOGNAME
> seed
> $ LOGNAME=bob
> echo $LOGNAME
> bob
> $ strings /proc/\$$/environ | grep LOGNAME
> LOGNAME=seed
> $ unset LOGNAME
> $ echo LOGNAME
> 
> $ strings /proc/\$$/environ | grep LOGNAME
> LOGNAME=seed
> ```

- A child inherits 2 types of environment variables from a shell parent: *Shell variables* and *exported user-defined shell variables*. Other shell variables are not passed down to child as depicted below.
![](Pasted%20image%2020221118105959.png)

## Attack surfaces

> Any data channel that flows from an untrusted entity to a trusted one is a potential attack surface. [Set-UID programs](Set-UID%20programs.md) are typically started from a non-privileged parent process, that means it gets its environment variables from a non-privileged process. If a Set-UID program or the libraries and the external programs invoked by that program uses its environment variables, it will be using untrusted input data from a non-privileged user.

### 1. Through [Dynamic Linker](Dynamic%20Linker,%20Dynamic%20Loader.md)

**Case study:** **Setting *LD_PRELOAD* and *LD_LIBRARY_PATH*** (environment variables that tell Linux dynamic linker where to find shared libraries) to control which libraries will be linked to a program. However this attack **does not work against Set-UID programs**.

### 2. Through external programs

**Case study:** **Modifying the *PATH* variable** to control which external program will be invoked if the program's code uses `system()` without specifying the full path to the external program.

### 3. Through application code

**Case study:** Modifying any environment variables that are used by `getenv()` in a program's code to control the program's input.
