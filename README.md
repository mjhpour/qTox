toxgui
======

For-fun Tox client that tries to follow the Tox UI mockup while running on all major systems. <br/>
This GUI uses code from @nurupo's ProjectTox-Qt-GUI, in particular the "Core" Toxcore wrapper. <br/>
However, it is not a fork.

<h2>Features</h2>

- One to one chat with friends
- Group chats
- File transfers, with previewing of images
- Audio calls
- Video calls
- Tox DNS

<h2>Requirements</h2>

This client will run on Windows, Linux and Mac natively, but binairies are only be provided for Windows at the moment. <br/>
Linux and Mac users will have to compile the source code themselves.

<a href="https://jenkins.libtoxcore.so/job/tux3-toxgui-win32/lastSuccessfulBuild/artifact/toxgui-win32.zip">Windows download</a><br/>
<a href="http://speedy.sh/XXtHa/toxgui">Linux download (1st July 2014 01:30 GMT)</a><br/>
Note that the Linux download has not been tested.
<br/>

<h3>OSX Install Guide</h3>

<strong>This guide is intended for people who wish to use an existing or new ProjectTox-Core installation separate to the bundled installation with toxgui, if you do not wish to use a separate installation you can skip to the section titled 'Final Steps'.</strong>

Installation on OSX, isn't quite straight forward, here is a quick guide on how to install;

The first thing you need to do is install ProjectTox-Core with a/v support. Refer to the INSTALL guide in the ProjectTox-Core github repo.

Next you need to download QtTools (http://qt-project.org/downloads), at the time of writing this is at version 5.3.0.
Make sure you deselect all the unnecessary components from the 5.3 checkbox (iOS/Android libs) otherwise you will end up with a very large download.

Once that is installed you will most likely need to set the path for qmake. To do this, open up terminal and paste in the following;

```bash
export PATH=/location/to/qmake/binary:$PATH
```

For myself, the qmake binary was located in /Users/mouseym/Qt/5.3/clang_64/bin/.

Once this is installed, do the following;

```bash
git clone https://github.com/tux3/toxgui
cd toxgui
qmake
```

Do not run make, as we need further modifications to toxgui.

Open up the Makefile in a text editor (TextEdit/TextWrangler, etc).

You will need to modify the Makefile to point to your toxcore libs/includes.

The first change you will need to make is to point the Makefile towards the tox libs installed on your system. (Generally this is /usr/local/libs/).

Look for the line in the Makefile which references /toxgui/lib/libs/ and replace with the above).

The second change to Makefile is to add the location of the includes (On my system these were placed in /usr/local/include/tox/).

To do this, search for the INCLUDES line and add the following to the end;

```bash
-I/usr/local/include/tox/
```

Save the Makefile.

<h4>Final Steps</h4>

Open up TextEdit/TextWrangler/etc and open up the widget/filetransfertwidget.cpp file and add the following include;

```bash
#include <math.h>
```

This will stop toxgui failing to make under OSX.

The final step is to run 
```bash
make
``` 
in the toxgui directory, or if you are using the bundled tox core installation, you can use 
```bash
./bootstrap.sh
```
Assuming all went well you should now have a toxgui.app file within the directory. Double click and it should open!

<h3>Screenshots</h3>
<h5>Note: The screenshots may not always be up to date, but they should give a good idea of the general look and features</h5>
<img src="http://i.imgur.com/mMUdr6u.png"/>
<img src="http://i.imgur.com/66ARBGC.png"/>
