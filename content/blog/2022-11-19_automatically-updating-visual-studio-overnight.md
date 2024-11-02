---
title: "Automatically updating Visual Studio overnight"
date: 2022-11-19T11:19:33-08:00
draft: false
---

A while back I ran across the [dotnet-vs](https://github.com/devlooped/dotnet-vs) project by [Kzu](https://www.cazzulino.com/about/). It's a super handy set of tools for VS from the CLI. 

I noticed it had an [`update`](https://github.com/devlooped/dotnet-vs#update) command which led me to immediately see if I can have use it to automatically update Visual Studio overnight. 

Here's how I set it up:
1. Install [dotnet-vs](https://github.com/devlooped/dotnet-vs) using the following command on the terminal: 
   * `dotnet tool update -g dotnet-vs`
2. Open up [Task Scheduler](https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page) and create a new *Task*.
3. Enable the following two options:
   * *Run only when user is logged on* 
   * *Run with highest privileges* 
4. Add a *Trigger* so the task runs early each morning. 
5. Add an *Action* to run `dotnet-vs`
   * Set *Program/script* by browsing to `%USERPROFILE%\.dotnet\tools\vs.exe`
   * Set *Add arguments* to `update all`

That's all I needed to do to start each day with the latest bits installed. Even if I leave Visual Studio running overnight, the installer will gracefully close and reopen it after the update. It's worked really well for me. 

Finally, this isn't something I'd say is officially supported. It's just something I tried and found to work. YMMV, but I hope it helps.