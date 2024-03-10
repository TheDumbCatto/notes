Determines how function parameters are passed from the caller to the callee. Usually, parameters may be passed to the callee via [Stack memory](Stack%20memory.md), registers, or both.
- **cdecl**: Caller cleans the stack
- **stdcall**: Callee cleans the stack (RET x where x is the no of bytes to wipe off of the stack)
- **fastcall**: Takes parameters via EDX & ECX (so the function uses the 2 w/o having to init any of them)
- **thiscall**