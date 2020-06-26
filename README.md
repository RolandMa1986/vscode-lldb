# Abaut
While learning CLR Runtime, I found it's hardly to understand how the context is switched between Managed and Nitave Code.

When I choose codelldb or cppdbg debugger to launch the app(in vscode), I can neither set the breakpoint on C# code, nor see the Managed CallStack.

You can not get Native frames if you are using coreclr debugger.

# SOS
Sometimes I will use [SOS](https://github.com/dotnet/diagnostics) plugin with lldb. but all the command was executed outside of the vscode.
So why not bring codelldb and sos together?

# Changes
- When initializing the lldb. SOS will be loaded.
- Check file's extention. use bpmd command instead if it's a cs file.
- Try find managed frame by IP2MD command if no source code is found when breakpoint is hit.

# Quick Start
Here's a minimal debug configuration to get you started:
```javascript
{
    "lldb.launch.debugServer": 4711,
    "lldb.launch.initCommands": [
        "plugin load /home/path/to/sos/libsosplugin.so",
        "setsymbolserver -ms"
    ],
}
```

# Links
- [Initial Setup](https://github.com/vadimcn/vscode-lldb/wiki/Setup)
- [Debugging in VS Code](https://code.visualstudio.com/docs/editor/debugging) - if you are new to VSCode debugging.
- [CodeLLDB User's Manual](MANUAL.md) - about this specific extension.
- [Troubleshooting](https://github.com/vadimcn/vscode-lldb/wiki/Troubleshooting) - known problems and solutions.
- [Q & A](https://stackoverflow.com/questions/tagged/visual-studio-code+codelldb) - for when you are stuck.



