## What is this?

This is a list of all the projects I've started, done a little work on, and gotten stuck / distracted before being ready to really consider them "finished". Except where otherwise noted, these are all web apps, with vanilla JS and CSS on the frontend, and [twelve-factor](http://12factor.net/) Node.js on the backend (if any). All of them have some degree of presence on GitHub.

[File an issue on this repo](https://github.com/stuartpb/help-wanted/issues) if any of these sound like something you'd like to help with.

## [Plushu](https://github.com/plushu)

A plugin-based command-line tool for crafting a user account on a host that can perform high-level dev/ops tasks. It goes hand in hand with a set of plugins (collectively, "Plus**k**u"), which create a mostly Heroku-compatible application deployment system (minus the "scaling to multiple hosts" part).

Right now, it's still pretty much in the "only the person who wrote this should use it" stage of development, since it doesn't really have a solid update mechanism, and I'm planning on introducing a few more breaking changes before I consider it "ready for public consumption".

### What needs to be done

For one thing, Plushu could use a better description of just what exactly it's  supposed to be. (I didn't even mention the way that everything is written entirely in Bash.)

Description aside, [here's every open issue across every plugin across the entire organization](https://waffle.io/plushu/plushu). I'd like to get the highest, biggest items in the "Under Consideration" list closed (specifically relating to "setup" bundles of plugins, so Plusku can have a solid future-facing upgrade path), then publish some kind of how-and-why guide explaining how to set it up.

## [Open Profilogical Web Survey](https://github.com/opws)

This is a project to map out the user account systems of every site on the web, from the URL of the registration page, to the requirements on passwords, to whether it accepts email addresses as a user ID.

### What needs to be done

I've written a *lot* of profiles for this, and a fair amount of tooling (it was my Project of the Month, for the one month where I tried to hold to such a thing): what it could *really* use is just a second contributor, or somebody else *using* it. 

## Various [Alphabinary Encoding](https://github.com/alphabi) projects

So, basically, if you take the modern Latin alphabet, map the first thirteen letters to 0, and the last thirteen letters to 1, you've got a workable vocabulary to represent any binary data as a series of English words. There are *so many things* you can do with this, and I'm frankly kind of amazed that I seem to be the only person who's recognized and thought about this (after a lot of Google searching of the key words in describing it came back completely empty).

The big obvious one is generating mnemonics for large numbers like hashes and crypto keys, but you can *also* use it to represent long-form data in a way that is *intrinsically* an expression of free speech, like the [DeCSS haiku][], but without having to make the data itself the subject of what you're writing.

[DeCSS haiku]: https://en.wikipedia.org/wiki/DeCSS_haiku

### What needs to be done

Honestly, I just want people to start *talking* about this. Beyond that, I do kind of wish I had some kind of authorship tools, like a text editor that makes suggestions of appropriate words that would fit the next bits in a sequence: I've got a Lua script that looks up all the words that match a sequence written so far, but nothing that hones in on things like *meaning*, like a thesaurus.

## [BizPostcard](https://github.com/bizpostcard)

I've never had an exchange of business cards generate an actual lead. What *has* worked for me has been handing my phone to the person I want to get in touch with, having them enter their email address, and sending them an email recapping what we talked about and what the next steps could be. I've drawn up a [pretty rough-shod icon for identifying the app](https://github.com/bizpostcard/bizpostcard-logo/blob/master/bizpostcard-icon.svg), which I would firmly classify as "good enough for now".

This would need a Node server for the account-verified emailer, as well as a CouchDB server for the user data. (The client'd talk to the CouchDB server for the single-page app's data, then POST to the mailer for sending the actual message). The mailer-server would probably also handle tasks like rendering and account management.

### What needs to be done

No code towards the implementation above has been written. The configuration for sending mails on behalf of the logged-in user needs to be sussed out in a way that won't cause messages to be blocked as spam. And account management, as always, is a beast.

One thing that doesn't require any programming but would be *hugely* helpful, even without this app, is [a repository of generic introductions](https://github.com/bizpostcard/stock-emails)

## [DingRoll](https://github.com/dingroll)

A chat platform that uses tags instead of channels, and keeps an edit history for all messages.

There's a bunch of design dialogue about this (read: me chatting to myself) at https://dingroll.slack.com - invites available on request. So far, I've coded [a tool for creating tag-based versions of conversations based on messages for Slack](https://github.com/dingroll/dreamcopter), for establishing an initial pool of content. I've also drawn [a fun little logo](https://github.com/dingroll/dingroll-logos/blob/master/dingroll.svg).

I'm thinking this'll be implemented with two Node server apps: one for serving the client, which will mostly just be a glorified caching proxy, and one for a realtime API server that takes engine.io connections (via Primus) and talks to RethinkDB.

### What needs to be done

While backend-wise I've written a chat app with the realtime architecture I described above before, I haven't written any code for DingRoll proper since *very* early in the project's conception. The server should be pretty straightforward to develop, though account management, as always, is a beast.

On the client, there are a couple bespoke UI elements that will take a bit of magic (`pointermove`, `contenteditable`, `position: absolute`) to implement (the tagging UI, and the history / scrollback buffer UI).

There's also pretty much no design work toward a UI that would be usable on mobile.

## [Tabalanche](https://github.com/tabalanche)

A Chrome extension that lets you save extra tabs that you're not using to a list, for access later. (Or not! Due to its PouchDB backing, you can stash *thousands* of tabs, *without any penalties* if you just keep them around and
*never look at them again*!) It's [currently available to install from the Chrome Web Store](https://chrome.google.com/webstore/detail/tabalanche/bmdmojejipbodfjbnennbnakhpboaoje), complete with a [nice icon](https://github.com/tabalanche/tabalanche-assets/blob/master/tabalanche-icon.svg) that carries through as a visual metaphor for icons in the popup UI.

### What needs to be done

I want to add a feature for users to sync their list of tabs to the cloud, but, to do this, I need to implement a system that will allow users to create accounts, because account management, as always, is a beast.

It'd be cool if the icon didn't use so many gradients.

## [Pull Tool](https://github.com/pulltool)

A Chrome app that makes cloud development of Chrome extensions significantly easier - indeed, I would say that it's easier to develop Chrome apps in the cloud with Pull Tool than it is to develop Chrome apps locally without it (ESPECIALLY on ChromeOS, good golly). Like Tabalanche (for which it was originally written, more or less), it is [available for install from the Chrome Web Store](https://chrome.google.com/webstore/detail/pull-tool/kldjpnhfppcfdinhcgfflnobfamjgdmf).

## What needs to be done

The UI could use a fresh coat of paint - while there's some smart modality in place to make sure that only relevant controls are presented to the user at any given time, it's still not as attractive as it could be, and most (all) of the UI is unlabeled, even where an unobtrusive label could significantly improve clarity.

The configuration format needs to be documented, since right now I'm the only one who knows how to do anythnig with it. In fact, EVERYTHING about how to use this tool needs to be documented in some series of YouTube videos or screencasts or blog posts or something. (Maybe there should be a blog for this.)

The API for triggering pulls needs to be improved before this can really be useful for interoperability with an extension like [rejig](https://github.com/pulltool/rejig).

The "database" of items, which is currently implemented as a single awkward array in chrome.storage.local, would work better as a PouchDB of independent documents that can't inadvertently overwrite each other.

## [Blotpass](https://github.com/blotpass)

A password store that is secured by your imagination. Unlike traditional password stores, Blotpass doesn't store your actual password: it generates a visual inspiration for you to come up with a password (based on the hash, via [Hashblot](https://hashblot.com/)), and saves only whatever *hint* you wish to give yourself to jog your memory the next time you need the password. If for some reason you lose access to the database of hints (eg. you're on somebody else's computer), you're not locked out of your account: since the inspiration is derived from the hash, it can be reconstructed from any device using your email address and the domain (since the password is *how you interpret an inkblot*, this doesn't leak any information) - even if the site itself is obliterated (due to the fundamental simplicity of the Hashblot algorithm).

### What needs to be done

I've made a rough implementation of a Chrome extension for this, but the UI needs some visual polish.

This also needs the same work toward cloud-synchronizable user data as Tabalanche - a mechanism to log into the site without having the extension installed would also be useful. Account management is, as always, a beast - even more than usual, due to the increased security sensitivity of the data in question.

## [NilPass](https://github.com/nilpass)

As interesting as Blotpass is, and as useful as it is on sites where you need easy access with a memorable password, it's overkill to use it for *every site*. What I really want, for most sites, is [passwordless login](https://passwordless.net/), using a link sent by email. Most sites don't implement passwordless.js directly, but you can effectively *emulate* the passwordless-login experience by abusing the "Forgot Password" feature. Nilpass would, consequently, be the most secure password manager possible: to log in to a site, you click the NilPass button to send a password reset email, then follow the link to the password reset page. On the reset page, Nilpass automatically generates a password, similarly to how most password managers would, then (after logging in with the new password, if necessary) **immediately forgets the password**, making it so the "Forgot Password" path is the *only* way to gain access to the account in the future.

### What needs to be done

I launched the extension itself, and [a homepage explaining it](https://nilpass.com/), on April 1, 2017. (For some reason, nobody paid attention to it.) I threw it all together in under 24 hours, though, and the UI could use a layer of polish.

The next steps for this, after polishing the UI a little, are to integrate data from the [Open Profilogical Web Survey](https://github.com/opws) and/or some heuristics to reduce the number of clicks involved in activating the password reset flow as low as possible. The ideal flow would be that, on clicking a "Log in with NilPass" link, the browser would automatically:

- go to the "password reset" page
- fill in the "password reset" form and submit it
- watch for the password reset email to arrive
- follow the link from that email
- fill in the "new password" as required to set a new password and log in
- forget the current password

Currently, only the last two steps are handled by the extension, and they both require a manual click from the user.

I've also been thinking that it might make sense to merge the functionality of Blotpass into this, instead of trying to develop two separate extensions.

## [PlugMap](https://github.com/plugmap)

A user-curated map of publically-available power outlets. It's one of the first apps I ever wrote.

### What needs to be done

Because this was written so long ago, it's using MongoDB, in all its awkward, joinless glory. Revisiting this, the first thing I'd want to do is yank that out and replace it with [RethinkDB](https://rethinkdb.com/).

The API endpoints don't have any sort of validation in place. That'd be one of the first things I'd want to fix.

I generally try to only code against open-source-implementable technologies, to avoid vendor lock, but I *still* don't know of any good way to store binaries like images other than the Amazon S3 API. I console myself with the knowledge that, if push comes to shove, it could technically be done by figuring out how the heck to implement Ceph, but what I'd *really* like to see is someone building an even simpler blob storage service around a simple open daemon like [SeaweedFS](https://github.com/chrislusf/seaweedfs).

While PlugMap has account management implemented, registrations are restricted, and the whole system is kind of hacky, as account management is, as always, a beast.

## [Flavored Markdown](https://github.com/flmd)

A site that tackles the proliferation of Markdown variants, not by scorning their differences and looking to quixotically invent [one universal standard that covers everyone's use cases](https://xkcd.com/927/), but by *documenting the differences between the standards*, and making it simpler to roll your own Markdown variant based on taking and leaving the different mutations of features that have developed across dialects.

### What needs to be done

Some deeper analysis of different variants of Markdown, beyond just posting links to their specifications and/or documentation.

## [Clipsnail](https://github.com/clipsnail)

There used to be a really awesome service called Clipboard, which had this Chrome extension for capturing content from a page, basically like a Pinterest for HTML (and with a bunch of needless wonkiness that seemed to be attempting to cover up the fact that the DOM tree exists). However, in 2013 they [ascended to the final phase of their incredible journey](http://ourincrediblejourney.tumblr.com/post/50250443285/clipboard) and were never heard from again.

It was really cool while it lasted, and I want to bring it back, with fewer leaky models, fewer hidden details, and [a logo so apropos, you'd think I didn't just pick the name randomly](https://github.com/clipsnail/clipsnail-logos/blob/master/chrome-icon.svg).

### What needs to be done

The Clipper extension needs essentially everything beyond the basic manifest and ability to target an element to be implemented.

The backend needs to be written (the little work that's presently on it was written in the VERY early, pre-auth days of RethinkDB).

Account management, as always, is a beast.

## [Chatphrase](https://github.com/chatphrase)

A browser-based video chat site with *no* account management, instead using arbitrary phrases to identify the party to connect to. (This was a really clever idea in mid-2013, before talky.io, appear.in, and every other WebRTC demo under the sun did it.) It's [purple][Chatphrase logo].

[Chatphrase logo]: https://github.com/chatphrase/chatphrase/blob/master/static/icon.svg "dammit marie they're minerals"

### What needs to be done

The WebRTC code hasn't been touched in years, is almost certainly broken, and needs to be brought up to speed with the interface defined in the most recent specifications.

I think HTTPS is broken, which is a problem considering the HTTPS-only restriction that's been in place on WebRTC since the end of last year.

The overall client interface is missing many useful features, like error handling, text chat, muting, or hanging up.

The signaling system (implemented as a standalone app) is rather needlessly fragile, and could be made less use-case-specific and tight in its design (complete with some kind of thumbnail-providing, multiple-potential-partner lobby system).

## [License In Three Lines][LITL]

[LITL]: https://github.com/litl-license

The "this code is free, but I'm not responsible for what happens" essence of the MIT license, boiled down to three lines.

The actual text of the license itself is done, as well as a rudimentary GitHub Pages site, and a [spiffy little logo](https://github.com/litl-license/litl-license/blob/gh-pages/logo.svg).

### What needs to be done

I need a blog post, or something like that, explaining the ideas and rationale around this license. Some links to existing blog posts talking about how software licenses are generally not enforceable, and how FOSS licenses are usually just a social signifier of what you'd *like* people to do with your code. Also, it'd be nice to have some forum for discussion to point readers to, although that'd probably just be Hacker News + Reddit + GitHub Issues.

I'd also like to credit the guy who originally had the LITL idea a little more prominently.

Some list of projects using the LITL would be nice, too (this can probably be done on the repo wiki).

## [Accouch](https://github.com/accouch)

This would be a standalone app exclusively for account management (which, you may have heard, is a beast). It could be configured and deployed to live alongside any other app, or as a third-party service.

### What needs to be done

All of it, including the basic architecture and design. This doesn't even have a logo.

## And many, many more

Ask me about [issue #1](https://github.com/stuartpb/help-wanted/issues/1).
