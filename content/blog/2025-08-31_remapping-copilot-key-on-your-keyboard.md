---
title: "Remapping your keyboard's Copilot key to END key (and others)"
date: 2025-08-31T11:32:51-07:00
draft: false
---
This was a bit of a frustrating journey, so writing it up here in case it helps others running into the same frustration. 

I've become accustomed to remapping the two keys immediately to the right of the spacebar on my keyboards to `HOME` and `END` (in that order). Usually that means mapping the `Right ALT` key to `HOME` and the Windows Menu (or right-click context menu) key to `END`. However, my two newer laptops replaced the latter button and introduced a new `Copilot` button. It turns out that one hasn't been as straightforward to remap, but I did finally find a way. 

The only way I've gotten it to work so far is to use [Microsoft PowerToys](https://learn.microsoft.com/en-us/windows/powertoys/install#install-with-windows-executable-file-from-github). Once installed, follow these instructions to get it set up:

1. Open up PowerToys settings
2. Expand the `Input / Output` section
3. Select the `Keyboard Manager` tool
4. Turn on the `Enable Keyboard Manager` option
5. Click on `Remap a shortcut` which will open a new window
6. Click on the `+ Add shortcut remapping` 
7. Click the pencil icon on the left side
8. Press the `Copilot` key on your keyboard
9. Click on the `OK` button to go back to the `Remap shortcuts` screen
10. Click on the pencil icon in the center of the window (under the `To:` heading)
11. Press the `END` key on your keyboard (including any additional keys you need such as Fn on many laptops)
12. Click on the `OK` button to go back again
13. Click on the `OK` button in the top right of the `Remap shortcuts` window
14. You're likely to get a warning message of some kind, but it should be okay to ignore (e.g., something about the `F23` key not being mapped)

You should be good now. In my case, I also remapped the Right ALT key to HOME. That one can be done by just using the `Remap a key` feature, so it's a little bit simpler. In the end, you'll end up with the following:

![PowerToys screenshot after setting up the two remappings.](/blog/images/2025-08-31_powertoys_1.png)

## More about the journey
You'll notice in the screenshot that the Copilot key maps to `Left Windows + Left Shift + F23` key combo. I first tried to just update my AutoHotkey script that I use on all of my PCs to map that combo to End by simply adding a line such as `#<+F23::END` to it. However, it seems a SHIFT key would still keep getting through which meant instead of just an `END`, I'd get a `SHIFT`+`END` combination. That means that Windows would *select* the text between where the caret started off and the end of that line instead of simply moving the caret to the end of the line. 

That led me to see if PowerToys would work. Less than ideal as it's nicer to keep all of this kind of config consolidated in one simple script I already have working on all of my machines, but still worth trying. I tried using the `Remap a key` support to map it (just like I described doing for the `RALT`->`HOME` key above), and it resulted in the same selection behavior I ran into with AutoHotkey. 

Somewhere along the way, I decided to try using the other `Remap a shortcut` feature instead. And it worked beautifully. Unfortunately, this took me several hours across an evening, a night's sleep, and the following morning to discover. I was determined to figure out a way to make it work even picturing myself having to write some lower level Win32 code (which has been ages since I did that) as I really couldn't see how this would be impossible to do. I still may end up spending some more time on seeing if I can get AutoHotkey to work for this case, but we'll see. For now, I'm just going to enjoy this little victory that would have driven me nuts for a long time to come.