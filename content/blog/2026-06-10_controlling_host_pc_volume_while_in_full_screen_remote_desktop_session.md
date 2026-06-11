---
title: "Controlling host PC volume while in full screen Remote Desktop session"
date: 2026-06-10T18:39:07-07:00
draft: false
---

I work in a full screen Remote Desktop (Dev Box) session daily, spanning two of my three monitors. A frustrating issue: when I press my volume keys or use a Fosi Audio VOL20 knob, they control the *remote* machine's volume instead of my host PC's speakers which are the ones that really matter. I wanted them to always control my local audio as that's what the remote session ends up piping through to anyway.

## The Journey

I started with what seemed like a simple AutoHotkey script using `#UseHook` to intercept volume keys. It worked but not when in full screen. If in windowed mode and with focus, it worked as I'd hoped. 

I tried several approaches:
- **Window detection** with `#HotIf WinActive()` couldn't detect full screen RDP windows
- **Admin privileges** didn't help
- **Keyboard remapping** with various combos:
  - `Ctrl+Alt+Arrow` was intercepted by RDP
  - `Win+Shift+Arrow` was also intercepted (and triggered window snapping in the remote session)
  - `Ctrl+Shift+F11/F12` was still captured by RDP

Full screen Remote Desktop seems to be pretty aggressive about capturing keyboard input. I'm guessing it operates at the driver level below where I was able to get AutoHotkey to intercept.

## The Breakthrough

Then I thought about how my Elgato Stream Deck volume controls work perfectly -- even in full screen RDP. It occurred to me that maybe it's because it doesn't send keyboard input - it probably uses direct API calls or USB HID events that RDP doesn't intercept.

This led me to try to use mouse input instead of keyboard input.

## The Solution

Mouse wheel input doesn't seem to be captured as aggressively as keyboard input. Here's the script I ended up with in the end. 

```autohotkey
#Requires AutoHotkey v2.0

; Use Ctrl+Alt+Shift+MouseWheel for host volume
; Works even when RDP is in full screen mode

^!+WheelUp:: {
    SoundSetVolume("+2")
    ToolTip("Host PC volume: " Round(SoundGetVolume()) "%")
    SetTimer(() => ToolTip(), -1000)
}

^!+WheelDown:: {
    SoundSetVolume("-2")
    ToolTip("Host PC volume: " Round(SoundGetVolume()) "%")
    SetTimer(() => ToolTip(), -1000)
}

; Ctrl+Alt+Shift+Middle Mouse Button = Mute Toggle
^!+MButton:: {
    SoundSetMute(-1)
    ToolTip("Host PC volume: " (SoundGetMute() ? "Muted" : "Unmuted"))
    SetTimer(() => ToolTip(), -1000)
}
```

**How to use:**
- **Ctrl+Alt+Shift + Mouse Wheel Up**: Increase host PC volume
- **Ctrl+Alt+Shift + Mouse Wheel Down**: Decrease host PC volume
- **Ctrl+Alt+Shift + Middle Click**: Toggle mute

The triple modifier combo (`Ctrl+Alt+Shift`) is one I'm hoping won't conflict with other applications while still being easy enough to get to. 

Now I can control my host PC's volume from within a full screen remote desktop session without having to exert myself tremendously by reaching for my Stream Deck. 😉 

As always, AutoHotkey scripts always take me on a bit of a trip that I'm quickly looking to end. It's highly possible I missed something along the way that would have been simpler. If anyone knows of a better way, I'd love to hear. 
