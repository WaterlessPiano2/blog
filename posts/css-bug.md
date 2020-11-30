---
title: "How I got stuck on CSS bug and how I fixed it"
date: "2020-11-28"
---

Last night I was following a tutorial on Youtube to create a navbar for my marketing site, so I can add more pages to it.
Then I got stuck on ["Designing with Tailwind CSS: Making the Navbar Responsive"](https://www.youtube.com/watch?v=qrTsS3z8BAw&feature=youtu.be&t=43). It really annoyed me as I could not figure out why it wouldn't work. I searched on Google for ages, and compared my code to examples, used sandboxes, and still couldn't figure out what was wrong. So I went to bed thinking about it.

When I woke up this morning, I straight away attempted to do the things that pop to my mind when I was in bed, and still no luck.
I described my problem on (Spoiler alert in the links) [Stack overflow](https://stackoverflow.com/questions/65049624/tailwind-css-smblock-class-is-not-overwriting-hidden-class-after-passing-th), [TailwindCSS github discussions page](https://github.com/tailwindlabs/tailwindcss/discussions/2933) and on TailwindCSS Discord page. It was my first time posting in these platforms so I wasn't too sure how long to wait. I ended up procrastinating on various other Discord channels I found. Seeing I am not going to do much today, I decided to go for a run. I twisted my ankle, and it is gone swollen.

When I got back, I was looking at my long list of things to do and remembered how unproductive today has been. I saw that I got an e-mail from Vercel saying they automatically deployed the pull request I created for demoing the bug. As I love procrastinating I decide to click the link ... like it's going to make any difference.

I was shocked to see that my deployed demo of the bug didn't have the bug in it...I was so confused, but also a relived as there are now more ways for me to find out the source of the bug. I instantly spin up the local copy and saw that the bug exists in the local version but not on the deployed version. They are both on the same branch so the code is exactly the same. I first thought maybe there is a caching of older CSS somewhere, or maybe the purge CSS is breaking this.

I opened the chrome dev tools to compare the CSS of the navbar on each item. It seems like in my local copy there is an extra display styling on the buggy element with `!important` property. It was in a section called injected styling, something I never heard before. Googling what it is, showed that it is something that some Google extensions can add to sites to work properly.
I confirmed this by running my local copy on incognito mode and on a different browser and not seeing the bug.

By removing all the extension on by one, I found that the "Dark Theme for Chrome" was causing this. Looking into this extension, this is how it works, it injects a bunch of styling to change the colours of the site. Removing this fixed my problem.

Now after all of that, I have a basic navbar. I guess I now learned another reason for UI bugs happening, and another thing to try when debugging UI problems. But was it worth it? It is a marketing site after all, and that is what WordPress and all the other website builders are for. They have tons of these components, premade. It takes the only couple of seconds to add them to your page.
Spending time, creating these components, take time away from the more important aspect of the marketing site. The content.
