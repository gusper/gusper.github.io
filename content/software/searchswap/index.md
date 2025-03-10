---
title: "SearchSwap"
date: 2022-11-27T18:07:16-08:00
draft: false
aliases:
    - /software/searchswap/
    - /searchswap
---
## Installation
Currently support Microsoft Edge and Google Chrome. I'll consider adding support for other browsers based on demand. 
* [Install for Microsoft Edge](https://microsoftedge.microsoft.com/addons/detail/searchswap/mhegncmnkpdckdpomfmedhflbfdkfpie)
* [Install for Google Chrome](https://chrome.google.com/webstore/detail/searchswap/meakfdkjiehkccdibhahjlgnihicmlel)

## Overview
SearchSwap is a browser extension that makes it really quick and easy to hop around different search engines and sites. E.g., imagine you're searching for something on Google but want to do the same search on Bing or Amazon. All you have to do is click on the SearchSwap extension icon on the browser's toolbar and then click on Bing, Amazon, or any of the other sites in the list. 

{{<rawhtml>}}
<img src="toolbar.png" width="70%" alt="SearchSwap extension icon on the browser's toolbar">
{{</rawhtml>}}

If you installed it but don't see SearchSwap on your toolbar, try clicking on the puzzle piece icon (the one immediately to the right in the screenshot above) as it's likely just not yet visible on your toolbar. I suggest you *pin* it so it's always just a click away on your toolbar.

Here's what the main window looks like. Simply click on the site you want to switch to, and SearchSwap will open up a new tab and repeat the same search on the site you clicked. 

{{<rawhtml>}}
<img src="searchswap-open.png" width="50%" alt="SearchSwap icon on the browser's toolbar">
{{</rawhtml>}}

I also added an Options page that allows users to add, delete, and modify (admittedly, a bit clunky now but will improve later) their list of sites.

{{<rawhtml>}}
<img src="edge2.png" width="60%" alt="SearchSwap icon on the browser's toolbar">
{{</rawhtml>}}

## Privacy
SearchSwap doesn't store or do anything with your search data (search terms, results, etc.). In fact, I built this extension when I couldn't find one like it that didn't also do all kinds of sketchy stuff. If you want to see how it works yourself, check out the source code for it below. 

## Source code
SearchSwap is Open Source Software and uses the [MIT license](https://github.com/gusper/SearchSwap/blob/main/LICENSE). For more information, visit our [GitHub repo](https://github.com/gusper/SearchSwap). 