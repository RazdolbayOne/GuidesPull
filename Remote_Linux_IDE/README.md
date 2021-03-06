
# Guides how to convert your IDE to remote one...
- [WHY I exist?!](#why)  
- [Turn your VSCODE into remote IDE |INTRO|](#visual-code)
  - [Step 0 ](#prepare-raspberry-pi)
  - [Step 1 ](#preparations-vscode)
  - [Step 2 ](#magick-can-start)
  - [Step 3 ](#magick-ingredients-aka-extensions)
- [FAQ ](#faq)
- [Turn your Microsoft Visual Studio into remote IDE |INTRO|](#mvs)
  - [What do you need to start:](#what-do-you-need-to-start)
  - [VS configuration part](#vs-configuration-part)
  - [Test project  ](#test-project)
- [Source list](#source-list)

## Why  
 Problem appiered when you start using Raspberry Pi as IDE .Its TOO SLOW!. In Raspbians VScode you do not have Intelsens(auto complite line.shows methodds of the class e.t.c), Debugger. This topic was created to solve this problems using remote build options in Visual studio or in VSCODE in the remote machines. where Raspberry PI will be used as compiler of programm.  

## Visual Code
<img src="https://imgur.com/N7XkVQk.png" height="65%"></img>  
Its assumed what you already installed [gcc](https://github.com/RazdolbayOne/GuidesPull/tree/master/Make/Makefile), [CMake](https://github.com/RazdolbayOne/GuidesPull/tree/master/Make/CMake), [Cutycapt](https://github.com/RazdolbayOne/GuidesPull/tree/master/A11Y%20progs#installation), [OpenVG](https://github.com/RazdolbayOne/GuidesPull/tree/master/OpenVG#installation-and-confuguration) etc on Raspberry.In version 1.42 (2020) of VsCode Microsoft still did not added ARM procesors support(no intellsans and debuging) but they said they will add in future [proof](https://github.com/microsoft/vscode-cpptools/issues/429),but they added remote IDE functionality. It means what you code projectfor example in ubuntu and use Raspberry Pi as compiler/linker.    
### Prepare Raspberry Pi  
* Pluged on Raspbbery and Enabled SSH   
    Start->Preferences->Raspberry Pi Configuration->Interfaces->["Enable SSH."](https://imgur.com/Qtg2m7v)
* Raspberry Pi hostname  
     Use this command in console to [get hostname: ](https://imgur.com/6urxqFa) 
     ```shell
     $ hostname -I
     ```
* Must be installed on Linux machine.command for installation(probably you can survive without gdb stuff):  
    ```shell
    $ sudo apt-get install openssh-server g++ gdb gdbserver
    ```
### Preparations VsCode  
Most importanly what allows you to turn your IDE as remote one (***install on client side***) is: 
* ["Remote Development"-Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)  


### Magick can start  
1.In VS Code, press on green rect(at the left lower corner)  
<img src="https://imgur.com/ErlhZxv.png" width="85%"></img>  
2.chose from popup window ***Remote-SSH connect to host***   
<img src="https://imgur.com/jiufgg0.png" width="85%"></img>  
3.For new conection press on "Add New SSH Host"    
<img src="https://imgur.com/aIg4UCN.png" width="85%"></img>  
4.VS will ask you to witch device to connect. in edit box enter connection request/command  
 example of input request
```shell    
ssh pi@${yours PIs hostname}
```  
<img src="https://imgur.com/X6tZc1X.png" width="85%"></img>  
5.VS will ask where to save/edit your .ssh config chose first one.  
5.1. inf .ssh config (see pic below how it looks like) you can rename your connection if needed change hostname/port/user etc  
<img src="https://imgur.com/mqbNM6i.png" width="85%"></img>    
6.press again on green rect to start session and chose needed conection  
7.VS will ask you password . enter pasword of remote  machine  
8.VS will do its magick(installation of vscode server etc)  
9.install on remote machine(press in vscode extensions tab) additional extensions(c++ language support,cmake support etc)  
10.press on Explorer (Ctrl+Shift+E) press on open folder button(you are now in yours pi cataloge LOL).  
11.??????  
12.PROFIT!  
 
[Microsoft readable source](https://code.visualstudio.com/docs/remote/ssh)  

### Magick ingredients aka extensions  
Installed [VsCode](https://code.visualstudio.com/) on your working machine not on Pi.  
Installed Extensions in VsCode server part:  
* ["C/C++ from microsoft"-debugger/intelsense/code browsing](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)   
* ["c/c++ definition" from regnofwebber-allows to create definitions like in vscode](https://marketplace.visualstudio.com/items?itemName=reignofwebber.c-cpp-definition-generator)    
* ["CMake"from trwxs -CMake languages support](https://marketplace.visualstudio.com/items?itemName=twxs.cmake)  
* ["CMake Tools" from Microsoft-Extended CMake support in Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)  
* ["CMake" from rwxs CMake language support](https://marketplace.visualstudio.com/items?itemName=twxs.cmake)   
* ["CMake tools" from MS extended CMake support](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) 
* ["Clang-Format" from xaver-is a tool to format C/C++](https://marketplace.visualstudio.com/items?itemName=xaver.clang-format) In vscode File->Preferences->Settings in search field type "clang" and in field change to google style  
<img src="https://imgur.com/OAY6D0n.png" width="85%"></img>  
now vscode will "force/help" you to write code in google code style  

* ["Commit Message Editor" from Adam Bender - allows better edit commit messages in conveniant way](https://marketplace.visualstudio.com/items?itemName=adam-bender.commit-message-editor)  
* ["Git history"- allows you to see what changed from previus commit compare version and more using git](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)  
  

### FAQ    
VSCode can be installed on windows.Can I use it in same way as in Linux?  
```shell  
ДА.
```
How you debug project?  
```c++  
printf("DEBUG style \n");  
```
How you use intelsanse if VSCode do not have ARM support? ->  
```shell  
under construction
```  
## MVS  
<img src="https://imgur.com/GoI1yZm.png" width="85%"></img>   
***THIS WORKS UNDER WINDOWS OS ONLY .***  (kinda tested on windows 7 and 10)  
[Maybe solution could be faund here](https://devblogs.microsoft.com/cppblog/linux-development-with-c-in-visual-studio/)
### What do you need to start
* N Straigth arms
* Pluged on Raspbbery and Enabled SSH   
    Start->Preferences->Raspberry Pi Configuration->Interfaces->["Enable SSH."](https://imgur.com/Qtg2m7v)
* Raspberry Pi hostname  
     Use this command in console to [get hostname: ](https://imgur.com/6urxqFa) 
     ```shell
     $ hostname -I
     ```
* crap what must be installed on Linux machine  
    command for installation:  
    ```shell
    $ sudo apt-get install openssh-server g++ gdb gdbserver
    ```
* [Installed Putty](https://www.putty.org/) on Windows  
* Obviosly installed MVS on Windows with Linux package  
in VS installer  
<img src="https://imgur.com/E8mP68t.jpeg" width="90%"></img>   
    	If needed install it  
	1)Start->Visual Studio installer  
    
	2)"in Installed page"   
		  more->modify  
        
	3)in "WORKLOADS"  
		scroll down and press on "Linux development with C++"  
      
	4)press "modify" button
    
	5)???  
    
	6)PROFIT!!!  
    
  

### VS configuration part
  1)Open MVS and chose "***Create new project***"  

 2)Chose "***Makefile Project***" if you havent it back to "***What do you need to start"*** ****punkt 6*** 

3)Write path where to store it on your machine  

  _*MVS migth show you pop out window where you need to enter Linux device info(hostname,user,password etc) fill it with info if it did not appiered its ok!_  
  4)***Connect your Linux machine to MVS:***  
  	In projec:Tools->Options->Cross Platform->press "Add button" fill pop out window with needed info(hostname,username e.t.c)  
	<img src="https://imgur.com/AkqclFk.jpeg" width="90%"></img>  
5)***Configure project to understand make for Make***  
	5.1)***Project type:***  
   		Project->$(Your project name)Properties..->General  
		Configuration Type->Makefile  
		<img src="https://imgur.com/v2Eol9F.jpeg" width="90%"></img>   
	5.2)***For compilator to understand***  
		Project->$(Your project name)Properties..->Remote Build  
		<img src="https://imgur.com/2rZ0yjd.jpeg" width="90%"></img>   
	5.3)***For Debuging***  
		Project->$(Your project name)Properties->Debugging   
		  Program->$(FULL_PATH_TO_EXE)/$(EXE_NAME)  
		<img src="https://imgur.com/49yik2S.jpeg" width="90%"></img> 
### Test project  
Create Source.cpp file in VS (it can be with different name I used this for guides purpose)
	in Source.cpp paste this code:  

```cpp
#include <iostream> 
	
int main(){  
	
	std::cout << "HELLO WORLD I AM ALIVE!@\n";  
	
	return 0;  
}
```
	
Create ***simple Makefile*** in project folder:  
```Makefile
#Something like that
	CC= g++ -g -Wall
	#compiling project and linking
	Hello:Source.o
		$(CC) -o $@ Source.cpp
	#command what allows you to delete obj files by using this command-> make clean
	.PHONY:clean
	clean:
		-rm *.o
```
   
   FINNALY PRESS CTRL+F5 then thru putty open yours project folder in linux machine and type this in console   
   ```
   $ ./$(Your project name.exe)  
   ```  

![wow](https://github.com/RazdolbayOne/GuidesPull/blob/master/Tunning%20MVS%20for%20remote%20linux%20projects/img/udivlenie.jpg)
  
## Source list  
### ENG
[Microsoft blog | ](https://devblogs.microsoft.com/cppblog/linux-development-with-c-in-visual-studio/)
[More MS blog | ](https://docs.microsoft.com/en-us/cpp/linux/download-install-and-setup-the-linux-development-workload?view=vs-2019)
[Even more MS blog | ](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.VisualCforLinuxDevelopment)  

### RUS
 [Habr | ](https://habr.com/ru/company/microsoft/blog/319962/)
 [ТЫК |](https://habr.com/ru/post/321228/)

### Archive  
[VSCODE template](https://imgur.com/DkHu53j)  
 
