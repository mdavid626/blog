---
layout: post
title:  "How to bring back old Notepad/Paint and Calculator on Windows 11"
date:   2024-12-15
tags: [windows, windows7, notepad, mspaint, calc, compatibility, windows11]
---

If you installed Windows 11 and you are like me, then you don't like the new Notepad and Paint. 

I extract them out from Windows 7, and it turns out, they work perfectly fine on Windows 11. 

You can download them from here: [https://blog.mdavid626.com/assets/windows7_notepad_mspaint_calc.zip](https://blog.mdavid626.com/assets/windows7_notepad_mspaint_calc.zip)

<!--more-->

You could extract the zip into a folder and run them from there. Don't forget about the `.mui` files (in the `en-US` folder). They are necessary for the apps to run.

I did disable the *App aliases* and uninstalled the new versions of Notepad and Paint. For Notepad this already brings back the old version, which might be already good enough to use. I also disabled the *App aliases* in *Settings* -> *Apps* -> *Advanced App Settings* -> *App execution aliases* for Notepad and Paint.

You could place `mspaint.exe` into `C:\Windows\system32`. As mentioned above don't forget to copy the `.mui` files.

It's a bit more complicated with `calc.exe` as the original owner of the file is set to `TrustedInstaller`, so it won't allow you to override/rename the file. You can change the owner to `Administrators` or `Users`. Then assign full control of the file to yourself, and you'll be able to override (or rename) the file.
