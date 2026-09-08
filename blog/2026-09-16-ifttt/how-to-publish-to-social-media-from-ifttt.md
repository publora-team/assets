# How to publish to social media from IFTTT

Connect Publora to IFTTT once, and anything IFTTT watches can go out to LinkedIn, X, Instagram, Threads, TikTok, YouTube, Facebook, Bluesky, Mastodon or Telegram. A blog feed, a web request, a row someone adds somewhere: it lands in your Publora queue and goes out from there.

It also works the other way. When Publora publishes something, IFTTT can tell you about it: a notification on your phone, a line in your records, a request to an endpoint of yours.

Twelve applets are ready to turn on, so you can see the whole thing work before building anything yourself.

### Before you start

You need an IFTTT account, a Publora account, and at least one social account connected inside Publora. IFTTT publishes through connections you already made, it does not create them. The Publora free plan covers 15 posts a month and three accounts and does not ask for a card.

On the IFTTT side, the Publora applets carry a Pro badge, so turning one on needs an IFTTT Pro plan. Their free tier runs two applets and does not cover ours.

### Connect Publora

1. Open [ifttt.com/publora](https://ifttt.com/publora) and press **Connect**.
2. A Publora window opens, shows which account you are authorising, and closes itself once you press **Approve**.

That is the whole setup. There is no API key to copy and nothing to paste.

![The Publora service page on IFTTT](https://raw.githubusercontent.com/publora-team/assets/main/blog/2026-09-16-ifttt/01-service.png)

*The service page. Connect sits here, and the applets are below it.*

### Turn on a ready-made applet

The service page lists twelve applets. Six of them feed Publora:

- **Share every new blog post** takes a new item from any RSS feed and publishes it.
- **Queue every new blog post** does the same but puts it in the queue instead of publishing straight away.
- **Turn new feed items into drafts** saves them as drafts so you can edit the wording first.
- **Post only the feed items that match a word** watches a feed for one keyword.
- **Publish, queue or save a draft from a web request** does the same three things from a webhook, which is the shortest path from your own code to a post.

![Twelve published applets on the Publora service page](https://raw.githubusercontent.com/publora-team/assets/main/blog/2026-09-16-ifttt/02-applets.png)

*Twelve applets, six in each direction.*

The other six report what Publora did: a notification when a post goes out or is queued, a daily or weekly email of everything published, and a web request to an endpoint of yours for record keeping.

Turning one on takes two fields: which feed to watch and which of your connected accounts to post to. The account list is read from your Publora account, so you pick a real channel, not a name you typed.

![An applet page with the Connect button](https://raw.githubusercontent.com/publora-team/assets/main/blog/2026-09-16-ifttt/04-fields.png)

*Each applet explains what it does before you turn it on. The Pro badge is IFTTT's, not ours.*

### Build your own applet

If none of the twelve fit, Publora gives you three actions and two triggers to combine with any other service on IFTTT.

**Publish a post** takes the text, the account, and an optional link to an image or video. The file has to be a public link: Publora downloads it on its side. Instagram, TikTok and YouTube always need one.

**Schedule a post** adds a delay before publishing: one hour, three, six, or a day. Useful when the trigger fires at an hour nobody reads.

**Create a draft** puts the post in Publora without a time on it. This is the one to use when the text needs a human pass before it goes out.

**New post published** fires when Publora publishes something. It gives you the text, the account, the network, the link to the attached file, the post id and the time. One post to three networks arrives as three separate events, so you can tell the channels apart.

**New post scheduled** fires when something lands in the queue. Handy when other tools fill your queue for you and you want to see what they added.

Publishing events reach IFTTT within seconds rather than on the hourly check, because Publora tells IFTTT about them as they happen.

### What comes out the other end

The event fields become ingredients you can drop into any other action. `{{Content}}` is the post text, `{{Account}}` is the channel name as you see it in Publora, `{{Network}}` is the network in lower case, `{{MediaUrl}}` is the attached file when there is one, and `{{OccurredAt}}` is the time.

A spreadsheet row of everything you published, a message in a team chat when a post goes live, a note in your own database: all of it is a matter of picking the second half of the applet.

### If something does not work

**The account list is empty.** IFTTT reads it from Publora at the moment you open the field. Connect a channel in Publora, then reopen the applet.

**The post has no image.** Check that the link is public and opens without a login. Publora fetches the file from that address, so anything behind a session will not reach it.

**Instagram, TikTok or YouTube refuse the post.** These three require media. A text-only post to them fails on their side, not ours.

**The applet ran but nothing appeared.** Open the post list in Publora. A failed post keeps its error there, and that message says which network refused it and why.

### One connection, ten networks

The point of putting Publora behind IFTTT is that the other services do not have to know anything about social networks. RSS knows about feeds, webhooks know about requests, your own code knows about your own events. Publora takes it from there.

[Connect Publora on IFTTT](https://ifttt.com/publora)
