In a team that has more than 1 developer working on the same project, comparing source codes can be an everyday task. Often times,we need to know the difference between two version of files in a branch or on different branch. Git gave use a bare bones tool right for the job, the ***git diff***. But as I have mentioned, its a bare bones approach. When dealing with lenghty files with multiple differences you will always prefer your go to diff tool  e.g. winmerge, kdiff etc. Luckily, GiHub supports this scenario using ***git difftool***.  In this post, we are configuring the git system to use KDiff  as the diff tool. You can go ahead and use other tool if you want too.

## What do we need?

- Git , of course.
- KDiff

## What do we need to do?

We only need to modify our ***.gitconfig*** file to include thwe configuration for the diff tool. If you dont have any diff tool installed, you need to install one or just stick with ***git diff***. 

```
git diff main dev
```

![Imgur](https://i.imgur.com/uV2aZkz.png)

For those interested in using ***KDiff***, the free software can be dowloaded at [their site](http://kdiff3.sourceforge.net/). Don't you just love visiting retro website like sourceforge :)

Open your ***.getconfig*** and add the following settings. For Windows user it probably sit in your users folder (e.g. C:\Users\[username]). Note that the example setting is for Windows.

```
[diff]
    guitool = kdiff3
[difftool "kdiff3"]
    path = C:/Program Files/KDiff3/kdiff3.exe
    trustExitCode = false
```

Once this is setup, we can now use KDiff3 as our diff tool when using git. 

```
git difftool main dev
```

This will launch KDiff3 where you can view differences as you always has been.

![Imgur](https://i.imgur.com/g5cJrc9.jpg)

Notice that git will prompt you everytime before it opens a file with differences.

![Imgur](https://i.imgur.com/PmqvTNS.png)

Or, you can specify the file yu want to compare

```
 git difftool main dev  -- .\daily-exercises\example1-main\Program.cs
```

Its a good thing ***git*** allows us to use our favorite tools for file diff operations. Otherwise, users who are more accustomed to GUI tools such as KDiff3 may have a hard time loving the system.