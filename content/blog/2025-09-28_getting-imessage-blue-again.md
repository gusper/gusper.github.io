---
title: "Getting iMessage Blue Again"
date: 2025-09-28T17:39:14-07:00
draft: false
---
We went to Europe a few months ago and set up temporary Europe-based eSIMs on our iPhones. They were simple to configure, worked great, and were definitely cheaper; it was totally worth the extra effort. The only hitch came when we returned to the States: a couple of us noticed that iMessage started sending and receiving texts as green bubbles (like when you’re messaging an Android user).

It turns out the switch back to your primary eSIM doesn’t always go smoothly. Sometimes Messages won’t fully re-register all of your identities (your phone number and email addresses). Here’s how we fixed it:

1. Go to `Settings` → `Messages` → `Send & Receive`, tap on `Apple Account` (email address), and `Sign Out`.
2. Go to `Settings` → `FaceTime`, scroll down, tap on `Apple Account`, and `Sign Out` there too.
3. Go to `Settings` → `General` → `Transfer or Reset iPhone` → `Reset` → `Reset Network Settings`. (This will erase saved Wi-Fi passwords.)
4. Your phone will restart automatically.
5. Reconnect to your Wi-Fi network.
6. Go to `Settings` → `Date & Time` and make sure `Set Automatically` is toggled `ON`.
7. Go to `Settings` → `Phone` and confirm that your correct number is listed next to `My Number`. If not, tap it and enter your full phone number.
8. Go to `Settings` → `Messages` and toggle `iMessage` back `ON`.
9. Go to `Settings` → `FaceTime` and toggle `FaceTime` back `ON`.
10. Go to `Settings` → `Messages` → `Send & Receive` and confirm all the identities under `You Can Receive iMessages To and Reply From` are checked.
11. Go to `Settings` → `FaceTime` and confirm all the identities under `You can be reached by FaceTime at` are checked.

In our case, the problem was that our phone number was unchecked—and grayed out—in the `Send & Receive` section. We couldn’t just re-check it. But after following all the steps above, the issue cleared up and everything started working normally again. Also note that sometimes we actually had to wait a bit for changes to propagate through the system. E.g., step 10 showed our identities as grayed out again at first but after a few minutes it was enabled again. 