# HttpUtils
![projectstage](https://img.shields.io/badge/project%20stage-release-green)
![projectstage](https://img.shields.io/badge/version-1.1-green)
[![license](https://img.shields.io/github/license/computercraft-package-tool/httputils)](https://github.com/computercraft-package-tool/httputils/blob/main/LICENSE)
[![issues](https://img.shields.io/github/issues/computercraft-package-tool/httputils)](https://github.com/computercraft-package-tool/httputils/issues)<br>
[![contributors](https://img.shields.io/github/contributors/computercraft-package-tool/httputils)](https://github.com/computercraft-package-tool/httputils/graphs/contributors)
[![activity](https://img.shields.io/github/commit-activity/m/computercraft-package-tool/httputils)](https://github.com/computercraft-package-tool/httputils/commits/main)
[![lastcommit](https://img.shields.io/github/last-commit/computercraft-package-tool/httputils)](https://github.com/computercraft-package-tool/httputils/commits/main)<br>
![size](https://img.shields.io/github/languages/code-size/computercraft-package-tool/httputils)
![files](https://img.shields.io/github/directory-file-count/computercraft-package-tool/httputils)
![languages](https://img.shields.io/github/languages/count/computercraft-package-tool/httputils)<br>

Library for the Minecraft mod **ComputerCraft/CC: Tweaked** including some additional HTTP Methodes  

## How to install 
HttpUtils can be installed using the [ComputerCraft Package Tool](https://github.com/computercraft-package-tool/ccpt) by using the following commands:

Install CCPT, only run if you havn't installed it yet:
```
pastebin run syAUmLaF
```
Install the library:
```
ccpt install httputils
```
The library will now be stored in "/lib/httputils.lua". It depends on the library [FileUtils](https://github.com/computercraft-package-tool/fileutils), which will be installed automatically with HttpUtils.

## How to use
### 1. **Include in your project**

The HttpUtils library can be included in your project by using the older ```dofile(...)```-method, or the newer ```require(...)```-method (availible only in [CC: Tweaked](https://tweaked.cc/)):

```lua
-- Using dofile(...)
local httputils = dofile("/lib/httputils.lua")
-- Using require(...)
local httputils = require("lib.httputils")
```

In both instances, the methods of the library can be accessed as members of the return value of the method, e.g. ```httputils.gethttpdata(...)```.

**Using *os.loadAPI("lib/httputils")* in order to include the library won't work anymore!** See also [deprecation notice](https://tweaked.cc/module/os.html#v:loadAPI) of the method.

### **2. Get table from URL**
https://github.com/computercraft-package-tool/httputils/blob/main/testing/testdata will be used in all examples:  
```lua
{
	greeting = "'ello"
}
```

The function **gethttpdata([url])** returns the parsed table fetched from the given URL. If an error occures, the errormessage is printed in console and false is returned.

*Example:*  
Code:
```lua
httputils = require("lib.httputils")
httputils.gethttpdata("https://raw.githubusercontent.com/computercraft-package-tool/httputils/refs/heads/main/testing/testdata")
```
Output:
<br><img
    alt="missing image :("
    src="https://raw.githubusercontent.com/computercraft-package-tool/httputils/main/img/getdata.png"
/><br>  

### **3. Download file from URL**  
The function **downloadfile([filepath],[url])** downloads a file from the given URL and stores it in the given filepath. If an error occures, the errormessage is printed in console and false is returned.

*Example:*  
Code:
```lua
httputils = require("lib.httputils")
httputils.downloadfile("test", "https://raw.githubusercontent.com/computercraft-package-tool/httputils/refs/heads/main/testing/testdata")
```
Output:
<br><img
    alt="missing image :("
    src="https://raw.githubusercontent.com/computercraft-package-tool/httputils/main/img/downloadfile.png"
/><br>  

Content of *"test"*:
```lua
{
	greeting = "'ello"
}
```

### **4. Get HTTP result from URL**  
The function **gethttpresult([url])** returns the raw result fetched from the given URL. If an error occures, the errormessage is printed in console and false is returned. It only differs from http.get([url]) because it does some additional error checking.

*Example:*  
Code:
```lua
httputils = require("lib.httputils")
httputils.gethttpresult("https://raw.githubusercontent.com/computercraft-package-tool/httputils/refs/heads/main/testing/testdata")
```
Output:
<br><img
    alt="missing image :("
    src="https://raw.githubusercontent.com/computercraft-package-tool/httputils/main/img/getresult.png"
/><br>  

## Changelog
- Update method to include the library using ```dofile(...)``` or ```require(...)```, as ```os.loadAPI(...)``` is (rightfully) [deprecated]((https://tweaked.cc/module/os.html#v:loadAPI))
- Add ```.lua```-extension to the library file (syntax highlighting in editors etc.). The only reason we did not have this before is that file extensions did not work with ```os.loadAPI(...)```, which is no longer supported with HttpUtils version 1.1 anyways.
- The library no longer lists [ProperPrint](https://github.com/computercraft-package-tool/properprint) as a dependency, which was erroneously listed but never used inside the library

## Last words
First of all, thanks for reading! This library is not the biggest library ever, but it turned out to be really useful for one of my projects, and maybe it is for yours too :)  
If you find bugs, please create an issue so I can fix them.  
I'm not that confident with GitHub yet, so feel free to point out things I could do better. Also, english is not my first language, so if you find any spelling/language-related mistakes, please do also create an issue.  
Have a nice day,  
PentagonLP
