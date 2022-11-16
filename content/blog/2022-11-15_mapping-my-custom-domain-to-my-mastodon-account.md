---
title: "Mapping my custom domain to my Mastodon account"
date: 2022-11-15T15:02:46-08:00
draft: false
---
I've been testing the [Mastodon](https://joinmastodon.org/) waters and started wondering if I should host my own Mastodon server. Didn't take much research to realize I wasn't as motivated *yet* to go all in, but I did run across [this post by Maarten Balliauw](https://blog.maartenballiauw.be/post/2022/11/05/mastodon-own-donain-without-hosting-server.html) which seemed an easy and worthwhile step to at least help on the discoverability front on Mastodon. He describes in detail how you can now search for him using his own domain and get routed over to his Mastodon account.

Coincidentally, right after I read Maarten's post, I saw a [post on Mastodon by Jeff Handley](https://mastodon.social/@jeffhandley/109349849358331062) where he was trying to get it working on [GitHub Pages](https://pages.github.com/) which is also where I host this site. A few minutes later he shared a link to his commit that had the necessary changes to make it work. 

Here's the changes I ended up doing to get it working for me:
* Add a folder to the root called `.well-known`. 
* Add a file called `webfinger` and save it in `\.well-known`.
* Add the following to the `webfinger` file: 

```
{
  "subject": "acct:gusper@mastodon.social",
  "aliases": [
    "https://mastodon.social/@gusper",
    "https://mastodon.social/users/gusper"
  ],
  "links": [
     {
      "rel": "http://webfinger.net/rel/profile-page",
      "type": "text/html",
      "href": "https://mastodon.social/@gusper"
    },
    {
      "rel": "self",
      "type": "application/activity+json",
      "href": "https://mastodon.social/users/gusper"
    },
    {
      "rel": "http://ostatus.org/schema/1.0/subscribe",
      "template": "https://mastodon.social/authorize_interaction?uri={uri}"
    }
  ]
}
```
* Add the following line to my `config.toml` file to get the `.well-known` directory published on the published GitHub Pages side:
```
include = ["/.well-known"]
```
Once deployed, folks can now search for `gus@gusperez.com` on Mastodon and get routed to where my Mastodon account is currently hosted `mastodon.social`.



