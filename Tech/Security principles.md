# Principle of data/code isolation
> **Data should be clearly isolated from code**

If the input is intended to contain only data, it should ONLY be treated as DATA. None of its contents should be treated as code.

If the input is a mix between data and code, there should be a clear mark to distinguish between the two.

-> This prevents not only attacks against Set-UID programs but also attack techniques like XSS, SQLi.

# Principle of least privilege
> **Every program and every privileged user of the system should operate using the least amount of privileges necessary to complete the job**

This introduces [POSIX capabilities](POSIX%20capabilities.md) which provides more granular capabilities to avoid the problem of over-authorizing a privileged entity.

Another implication is that any unnecessary privileged capabilities in the execution of a program should be disabled, and any privileged capabilities used in the duration of the execution should be wiped off after the execution. 

# Just-in-time access
- Privilege granted to access applications or systems is limited to predetermined periods of time, on an as-needed basis
- This helps to minimize the risk of standing privileges that attackers or malicious insiders can readily exploit.