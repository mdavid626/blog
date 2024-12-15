---
layout: post
title:  "Windows 7 notepad.exe, mspaint.exe and calc.exe"
date:   2024-12-15
tags: [windows, windows7, notepad, mspaint, calc, compatibility, windows11]
---

If you installed Windows 11 and you are like me, then you don't like the new Notepad and Paint. 

I extract them out from Windows 7, and it turns out, they work perfectly fine on Windows 11. 

You can download them from here: [https://blog.mdavid626.com/assets/windows7_notepad_mspaint_calc.zip](https://blog.mdavid626.com/assets/windows7_notepad_mspaint_calc.zip)

<!--more-->

You could extract the zip into a folder and run them from there. Don't forget about the `.mui` files (in the `en-US` folder). They are necessary for the apps to run.

Placing the files into `C:\Windows\system32` might not work, as Windows 11 doesn't allow you to override some files there (huh?). Additionally, you might need to disable `App aliases` in `Settings -> Apps -> Advanced App Settings -> App execution aliases`.
