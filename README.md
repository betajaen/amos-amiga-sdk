# amos-amiga-sdk



Written by Robin Southern @betajaen





These are automatically generated bindings from the official Amiga OS SDKs. The bindings are AMOS Procedures to call Amiga OS functions; such as Exec, Intuition, Graphics, and so on. These bindings are intended and written for AMOS Professional 2.0, although in other versions of AMOS could be usable but are not supported



The SDK is based upon V37.4 (Workbench 2.04).



Each Amiga library has it’s own `.Asc` file which needs to be turned into a `.AMOS` file.  This can be creating a blank file in the Editor and then merging ASCII from the Menu. Then just save the file with a `.AMOS` extension instead.



## Typical Usage



Using the Procedures aren’t for the faint-hearted. You should have experience with direct Amiga OS before hand, in particular Assembly programming.



To load in a library, include the binding file at the top of the AMOS source code.



```
Include "Work:amos-amiga-sdk/v37/intuition.AMOS"
```



The libraries have to be opened and closed in the traditional Amiga way.



```LIB_OPEN_GRAPHICS[1]
LIB_OPEN_GRAPHICS[1]
Print _GFX_BASE
LIB_CLOSE_GRAPHICS
```



The `1` argument refers to the Library Channel (See AMOS Professional User Guide 11.05.01), so in this case Channel 1. Each library needs it’s own separate channel, and I’ve found in experience to start at 1 and increment each time.



The Procedures themselves call the Amiga Functions directly via the `Lib Call` function. Not before filling in the CPU registers with the required parameters.



Each function name has been transformed into the AMOS Notation, and prefixed with an underscore to prevent name mangling. `LoadView` is `_LOAD_VIEW`, `SetSoftStyle` is `_SET_SOFT_STYLE`.



Arguments are always longs, which can be a pointer or a 32-bit number. Strings have to be passed in as pointers (see `Varptr`), as the Amiga OS functions have no idea of the internals of AMOS.



Finally if there is any return value, it is placed as usual in `Param`.



### Future



I would like to port over the structure layouts and constants over but due to how many there are, and how AMOS does not support constants they may have to be Global variables which isn’t an ideal solution.



I would also like to have a go at having a Workbench 3.1 version, to support AGA. I understand AGA support is a hot-topic when it comes to AMOS, so no promises. 





