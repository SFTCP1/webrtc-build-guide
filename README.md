Notice: We have launched [SwordFishTheChordedPlayer1 WebRTC](https://github.com/SFTCP1/webrtc) to get a WebRTC Static Binary from here

We will remove the original release soon.

# WebRTC
WebRTC - a library that enables users to add a real time communication capabilities into their C++ or JavaScript applications.

To build WebRTC From Source, you might need some components to build the library:
Build Requirements:
- Visual Studio 2019 with Desktop C++ Workload.
- Windows SDK 10.0.19041.0
- depot_tools 

1. Download Chromium depot_tools given [here](https://storage.googleapis.com/chrome-infra/depot_tools.zip) and extract it somewhere
2. Set depot_tools into the PATH enviroment variable
3. Run gclient. it downloads the CIPD Client and it's tools: Python and Git.
4. After you done that: Type
``` 
fetch --nohooks webrtc
```
Note: if it can't download, type:
```
fetch --no-history --nohooks webrtc
```
This command takes many hours to download.

5. After the command is finished, type gclient --runhooks to run the hooks.
6. Change into to the src/ directory
7. Type: 
``` 
gn args out/Default
```
This will open a text editor which you can add arguments here, see ```gn args out/Default --list``` for a list of arguments.
8. Copy and paste the arguments into text editor, then save and close.
```
is_component_build = false
is_debug = false
is_clang = false
```
9. After the command was done generating files, type:
```
ninja -C out/Default
```
This command takes many hours because of the unit-tests and sample applications.
If you want to disable unit-tests, just type only webrtc target
```
ninja -C out/Default webrtc
```
This should build the WebRTC library.
