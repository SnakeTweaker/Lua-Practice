Compiled Lua from source in VS2019. These files are for reference use only. Interpreter is fully functional and all libraries are linked to VS2019.

Steps:

1. Download latest version of Lua from https://www.lua.org/download.html
2. Save the tar.gz in a memorable location
3. Extract the tar.gz via Windows Powershell or 7zip/WinRar
4. Create your directory in your Program Files folder C:/Program Files/Lua
5. Create your include folder within this directory, copy and paste all the libraries from the Lua src folder
6. Create your VS C++ Empty project, add all the libraries to your source files with the exception of luac.c and lua.c
7. Change your compilation settings from debug to release and run it on x64
8. Right click on your solution and select properties, under the general tab you will switch configuration type from .exe to .dll
9. Under C/C++/preprocessor define your preprocessor and add "LUA_BUILD_AS_DLL;"... Build the solution
10. lua.lib and lua.dll will build, nav to your project folder under /lua/x64/Release copy both files and paste them into your directory C:/Program Files/Lua
11. The compiler will need to be built from here on...
12. Under project properties, delete "LUA_BUILD_AS_DLL" and change the config type back to .exe 
13. Add luac.c to your source files in VS2019and rebuild, the lua.exe will output to your Release folder, rename this file to luac.exe
14. Copy this file and paste it to C:/Program Files/Lua
15. Now to build the interpreter...
16. Remove all libraries from your source files section in the solution explorer
17. Add in lua.c, this should be the only file
18. In properties/C/C++ include directory C:/Program Files/Lua/include
19. Under linker/input/Additional Dependencies type in "lua.lib;"
20. Under linker/general/Additional Libraries Directories add directory C:/Program Files/Lua
21. Build solution, the executable should be output to the release folder, paste lua.exe to C:/Program Files/Lua, now lua source code and be compiled into lua bytecode
22. Congrats!
