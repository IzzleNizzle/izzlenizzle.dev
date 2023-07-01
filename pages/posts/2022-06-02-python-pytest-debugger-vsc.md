---
title: Testing w Python, Pytest, Debugger & Virtual Environment in Visual Studio Code
date: 2022-06-02T13:37:00.000Z
description: How I got Python testing with Pytest and a Debugger working in VSC
tag: web development
author: Isaac
---

So for awhile now I’ve been struggling to put this all together neatly. I’ve been using one command for testing and another for debugging my code. But today I finally put it all together and boy does it feel amazing!

![Tests Tab Debugger](/images/Debug_Test.png "Tests Tab Debugger")

So what not all my tests are passing lol. They are actually there in the tests tab!!! For so long I wondered what that thing was even for, or how it worked. Now I know!

And yes, now there’s this wonderful button that can run the test with a debugger. So I go and set a breakpoint, push the magic button, and boom my test runs correctly and pauses on my breakpoint for me to see what is going on. Wow, this feels great!

So how did I do this? Admittedly my solution was a bit of a hack. I first tried going through the settings, and googling some things, but I honestly could not find the happy easy path. I ultimately had to read the commands that Visual Studio Code (VSC) was trying to run and modify them a bit. 

### The nitty gritty:

An important piece to note, as this was confusing VSC: My project folder structure looks something like this

`project_name/app/test/test_api`

So I would have VSC open in the root folder, when I tried to use the Testing tab, I would set it up with “Pytest” as the testing framework, and then the folder for the tests would be “app”. It honestly would not allow me to choose a deeper folder than app. So after I clicked that button, nothing would happen.

So I eventually opened the /app folder in VSC like this:

`code app`

Now from this context, I was able to push those same buttons in the testing tab, but this time something happened as I was able to choose the “test/“ folder as the entry point for my tests. It seemed to pick those up, however there was still an error with it working correctly.

![Empty Tests Tab](/images/TESTING.png "Empty Tests Tab")

So I opened up the Output tab (Near the terminal tab) and started reading through. All my tests were failing because they could not find certain modules. I’ve seen this before so I recognized that this was an issue with the code not being ran from my Virtual Environment which has all my modules/packages set up. Still felt like progress.

So scrolling up on the Python Output page, I saw where the tests began to run, and I could see the command that VSC was using to try to set up the tests tab. It looked something like this:

`~/.pyenv/versions/3.9.7/bin/python ~/.vscode/extensions/ms-python.python-2022.6.3/pythonFiles/testing_tools/run_adapter.py discover pytest -- --rootdir . -s --cache-clear test`

Ok, very interesting. So I went back to my other VSC window which was opened at the root project folder. I opened a terminal and activated the Virtual Environment for this app. I got the location of the python file that runs inside that virtual environment with this command:

`which python`

It pointed to this python file

`/Users/izzlenizzle/.pyenv/shims/python`

I noticed that the code VSC was running was pointing to a different python file, so I figured I’d try just swapping out that python for the python file inside my virtual environment. 

So notably I was back in my root folder directory VSC window, as this was where I wanted to configure the Tests tab ultimately. I then needed to modify the command in one other place in addition to the python path.

I also updated the path to the test folder. I noticed that at the end of the command I pulled from VSC, there was an argument for “test”. I recognized that was the path for my tests, so I just updated that to the path to my tests from the context of my root project directory. Here is the ultimate command I used:

```/Users/izzlenizzle/.pyenv/shims/python ~/.vscode/extensions/ms-python.python-2022.6.3/pythonFiles/testing_tools/run_adapter.py discover pytest -- --rootdir . -s --cache-clear app/test```

This ran and outputted a rather large JSON string to the terminal. It appeared to have some information regarding my tests and there locations. That gave me the impression that something happened. I then opened my VSC Tests tab and to my surprise I could see the tree of my tests there! 🎊🎉

This honestly came as a surprise because I’ve been digging for a solution for a long time now. I tried digging around in different settings and googling around, digging through Github issues and comments there. But I ultimately found this solution. Now I realize it’s tacky, but I’m perfectly satisfied with finding this as it really helps me increase my development speed and reduce bugs.

I understand that switching virtual environments inside this project would likely mean re-initializing the tests tab, and that’s not a great experience. But if that were your situation, I imagine using the previous command with the updated path for the python executable would do the trick.

But if anyone is aware of the better way of doing this, I am open to hear it! Feel free to DM me on twitter.

Hope this helps!
