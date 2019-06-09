# Compiling Sven Co-op Maps

## Svencraft / Hammer Setup
Begin by download the Sven Co-op SDK using steam, launching the SDK (Svencraft) and creating a game configuration called **Sven Co-op**.

Configure paths accordingly, replacing **<steam_path>** and **<repos_path>** with your own drives/paths:

**Paths -> Game Executable**
```
<steam_path>\steamapps\common\Sven Co-op
```

**Paths -> Mod Directory**
```
<steam_path>\steamapps\common\Sven Co-op\svencoop
```

**Paths -> Game Directory**
```
<steam_path>\steamapps\common\Sven Co-op\svencoop
```

**Paths -> RMF Directory**
```
<repos_path>\svencoop-lentoman
```

**Textures -> Add Wads**
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\halflife.wad
<repos_path>\svencoop-lentoman\sc_frogger\textures\sc_frogger.wad
```

**Build -> Game Executable**
```
<steam_path>\steamapps\common\Sven Co-op\svencoop.exe
```

For build executables there are issues with spaces in path, first create a symbolic link by opening a new Command Prompt as administrator and using the following command:
```
mklink /J C:\sven-sdk "<steam_path>\steamapps\common\Sven Co-op SDK"
```

**Build -> CSG executable**
```
C:\sven-sdk\mapping\compilers\SC-CSG_x64.exe
```

**Build -> BSP executable**
```
C:\sven-sdk\mapping\compilers\SC-BSP_x64.exe
```

**Build -> VIS executable**
```
C:\sven-sdk\mapping\compilers\SC-VIS_x64.exe
```

**Build -> RAD executable**
```
C:\sven-sdk\mapping\compilers\SC-RAD_x64.exe
```

**Place compiled maps**
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\maps
```

## Installing Additional Map Files

Before compiling and running any of the maps, make sure any additional mapfiles are installed.

Copy the contents from a maps release folder into:
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\
```

## Compiling

To compile a map, importing or creating a batch / build configuration is recommended.

Optionally shut down Svencraft/Hammer and copy the 
```
<repos_path>\svencoop-lentoman\Hammer\CmdSeq.wc
```
to 
```
<steam_path>\steamapps\common\Sven Co-op SDK\mapping\hammer
```

Then open a .rmf map file then press the run button or F9 key in Svencraft/Hammer. Click the Expert button in the dialog that opens. If you copied the .wc script, make sure the **Sven Co-op (full)** config is selected, otherwise create a new config with the same name and the following commands:

Command: ```Change Directory```  
Parameters: ```$exedir```

Command: ```$csg_exe```  
Parameters: ```$path\$file -nowadtextures```

Command: ```$bsp_exe```  
Parameters: ```$path\$file```

Command: ```$vis_exe```  
Parameters: ```$path\$file -full```

Command: ```$light_exe```  
Parameters: ```$path\$file -extra```

Command: ```Copy File```  
Parameters: ```$path\$file.bsp $bspdir\$file.bsp```

Command: ```$game_exe```  
Parameters: ```+map $file -dev -console```

Finally click the **Go!** button

## Packaging Final Build Zip

After building and running, copy the .bsp file to the releases folder of the map you compiled and zip it manually.
