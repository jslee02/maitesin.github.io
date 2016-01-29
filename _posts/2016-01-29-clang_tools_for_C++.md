---
layout: post
title: Clang tools: clang-format, clang-tidy and clang-modernize 
category: Dev
tags: [C, C++, Clang]
---

**[Clang](http://clang.llvm.org/)** is a compiler front end for the C, C++, Objective-C and Objective-C++ programming languages. It uses [LLVM](http://llvm.org/) as its back end. It also has several awesome tools build on top of **Clang** and I am going to show the three of them I use the most.

As usual, I am working from an Arch Linux computer. Therefore, I can install **Clang** and the tools from the repository (clang, clang-tools-extra). For other distributions you can find the information in the documentation.

As always, **all the code used in this post is available in this [repo](https://github.com/maitesin/blog/tree/master/clang_tools_2016_01_29)**.

The videos are made with **[asciinema](https://asciinema.org/)**, that means **you can copy from the video**.

#Clang-format
This tool is **perfect to make sure that you are following a specific code style** and it is fully configurable.

It can be used integrated in your editor or IDE. In my case I have it integrated in my Vim configuration. You can see how it works in the following video:
<script type="text/javascript" src="https://asciinema.org/a/eas94n9bjs27c35xuix875xum.js" id="asciicast-eas94n9bjs27c35xuix875xum" async></script>

Original state of the code:
<script src="https://gist.github.com/maitesin/b5df2700cea555ac1864.js"></script>
After formatting:
<script src="https://gist.github.com/maitesin/c1baed4716e1c705ca66.js"></script>

#Clang-tidy
This tool is really useful to have it integrated with your **version control system**. I like to have it configurated **to run as a pre-commit hook**. In case it detectects any problem the commit fails. Therefore, you only commit code that has been aproved by the tool. As I use **CMake** I have to add a definition to generate the json file needed from the tool.
<script src="https://gist.github.com/maitesin/ab1e5b174817769022fd.js"></script>
After that the code can be analyzed for all checks as follows:
<script src="https://gist.github.com/maitesin/431f35fcce8275df739b.js"></script>
You can deal on your own with these problems, or let it fix them for you using the *-fix* flag.
<script type="text/javascript" src="https://asciinema.org/a/def6c40kpd94p12i6e207gd4m.js" id="asciicast-def6c40kpd94p12i6e207gd4m" async></script>

#Clang-modernize
Last but not least, this tool is made **to update old code to C++11**. This tool is not bullet proof, but it can make your job easier if you have to migrate the old code to newer standards. It has an option called *-risk* that can have three values: *safe, reasonable or risky*, by default it uses *reasonable*.

Old code:
<script src="https://gist.github.com/maitesin/fd8c3f63372db48afeb6.js"></script>
Modern code:
<script src="https://gist.github.com/maitesin/c08f7faa41f6ca453228.js"></script>

#Conclusion
**These three tools make your live easier as developer**. You will be sure you code is following the code style from your company/project, it will ensure that you are committing code that is using the new features from **C++11** and it will help you migrate the old code to use the features from **C++11**. I strongly recommend to include them in your workflow, because it will boost your work performance.

**NOTE: This post is based on version 3.7.1 from Clang. In version 3.8 clang-tidy will include from checks from clang-modernize. So, it will enforce you to use features from C++11**.