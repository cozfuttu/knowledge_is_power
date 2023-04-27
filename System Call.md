A system call is a mechanism used by a program to request a service or resource from the operating system [[kernel]]. It provides a way for user-level programs to interact with the [[kernel]], which is responsible for managing system resources such as memory, [[process]]es, and I/O devices.

When a program needs to perform a privileged operation, such as opening a file, allocating memory, or accessing a hardware device, it makes a system call to the [[kernel]]. The system call is typically initiated by a software interrupt, which transfers control from the user-level program to the [[kernel]]. The [[kernel]] then performs the requested operation on behalf of the program in [[kernel]] mode, where it has full access to system resources, and returns the result to the program in user mode.

System calls are an important mechanism for providing a standardized interface between applications and the operating system. They allow applications to access system resources in a controlled and secure manner, and provide a way for the operating system to enforce security policies and manage system resources efficiently.

Different operating systems provide different sets of system calls, each with its own parameters and semantics. Some common system calls include file I/O, [[process]] management, memory management, and network communication. System calls are typically documented in the operating system's manual or online documentation, and are often exposed to developers through programming libraries or APIs.