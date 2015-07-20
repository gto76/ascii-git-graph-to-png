Ascii Git Graph to Png
======================

Generates nice picture of the graph drawn in ascii art style. They say picture is worth more than a thousand words, so here you go:

### Input:
```
			origin/head origin/master
			          \ /
			     HEAD-(D)-master 
			         / | \
			       (B)(C) v1.0     
			        | /          
			       (A)         
			        |     
			       ---
```

### Output:
![Alt text](/doc/example.png?raw=true "Screenshot")

How to run on…
--------------

### UNIX
```bash
sudo apt-get install imagemagick
git clone https://github.com/gto76/ascii-git-graph-to-png.git
cd ascii-git-graph-to-png
./render-graph --example
display example.png
```

### Windows

* Download and install [wget](http://sourceforge.net/projects/gnuwin32/files/wget/1.11.4-1/wget-1.11.4-1-setup.exe/download)
* Open command prompt
* Go to the directory where you want Cygwin installed
* Install Cygwin:

>```bat
:: set path of wget
set PATH=%PATH%;C:\Program Files (x86)\GnuWin32\bin
:: download cygwin
wget --no-check-certificate https://cygwin.com/setup-x86_64.exe
:: install cygwin
mkdir cygwin
setup-x86_64.exe --quiet-mode --no-shortcuts --site http://cygwin.mirror.constant.com --root %cd%\cygwin -P ImageMagick -P bc -P git
::
```

* Download and run the app:

>```bash
cygwin\Cygwin.bat
# fix the missing fonts problem
cd /usr/share
mkdir fonts
cd fonts
ln -s /cygdrive/c/Windows/Fonts corefonts
# get ascii-git-graph-to-png converter and generate example image
cd
git clone https://github.com/gto76/ascii-git-graph-to-png.git
cd ascii-git-graph-to-png
./render-graph --example
# display image
cygstart example.png
#
```

Help
----
```
Usage: render-graph [OPTION]... [FILE]
Reads a graph from ascii drawing and creates PNG file using ImageMagick's 
convert command. Intended for drawings of git history graphs.

	-s, --size=SIZE
		set height of one cell in pixels, default value is 40.
		Will accept values between 2 and 62.

	-o, --output=FILENAME
		choose the filename for the output file. The .png suffix will
		be appended at the end of the name. Default output filename
		is the input filename with the .png suffix.

	-t, --tab-width=SIZE
		set number of spaces tabs in input file are gonna be 
		converted to, default value is 4

	-c, --no-color
		do not colorize the labels of the graph

	-h, --help
		display this help and exit

	-e, --example
		create picture from the example graph below. If output filename
		is not specified, it gets saved as example.png

			origin/head origin/master
			          \ /
			     HEAD-(D)-master 
			         / | \
			       (B)(C) v1.0     
			        | /          
			       (A)         
			        |     
			       ---

	-v, --version output version information and exit

Report bugs to https://github.com/gto76/ascii-git-graph-to-png/issues
Copyright (c) 2014 Jure Sorn. The MIT License (MIT).
```
