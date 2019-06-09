# Compiling Sven Co-op Maps

## Svencraft / Hammer Setup
Download the Sven Co-op SDK using steam

Create a game configuration, call it Sven Co-op.

Configure paths accordingly, replacing <steam_path> and <repos_path> with your own drive/path.

Paths -> Game Executable
```
<steam_path>\steamapps\common\Sven Co-op
```

Paths -> Mod Directory
```
<steam_path>\steamapps\common\Sven Co-op\svencoop
```

Paths -> Game Directory
```
<steam_path>\steamapps\common\Sven Co-op\svencoop
```

Paths -> RMF Directory:
```
<repos_path>\svencoop-lentoman
```

Textures -> Add Wads:
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\halflife.wad
<repos_path>\svencoop-lentoman\sc_frogger\textures\sc_frogger.wad
```

Build -> Game Executable:
```
<steam_path>\steamapps\common\Sven Co-op\svencoop.exe
```

For build executables there are issues with spaces, first create a symbolic link using:
mklink /J C:\sven-sdk "<steam_path>\steamapps\common\Sven Co-op SDK"

Build -> CSG executable:
```
C:\sven-sdk\mapping\compilers\SC-CSG_x64.exe
```

Build -> BSP executable:
```
C:\sven-sdk\mapping\compilers\SC-BSP_x64.exe
```

Build -> VIS executable:
```
C:\sven-sdk\mapping\compilers\SC-VIS_x64.exe
```

Build -> RAD executable:
```
C:\sven-sdk\mapping\compilers\SC-RAD_x64.exe
```

Place compiled maps:
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\maps
```

## Installing Additional Map Files

Before compiling and running any of the maps, make sure to install all additional files required by the maps.

Copy the contents from a maps release folder into:
```
<steam_path>\steamapps\common\Sven Co-op\svencoop\
```

## Compiling

To create a built a batch / build configuration is recommended.

Alternatively you can shut down Svencraft/Hammer and copy the <repos_path>\svencoop-lentoman\CmdSeq.wc to <steam_path>\steamapps\common\Sven Co-op SDK\mapping\hammer

Open a .rmf map file then press the run button or F9 key in Svencraft/Hammer. Click the Expert button in the dialog that opens. If you copied the .wc script, make sure the **Sven Co-op (full)** config is selected, otherwise create a new config with the same name and the following commands:

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

## Packaging Final Build Zip

After building and running, copy the .bsp file to the releases folder of the map you compiled and zip it manually.
