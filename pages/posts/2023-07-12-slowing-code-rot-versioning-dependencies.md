---
title: Avoiding Code Rot - Setting Dependency Versions
date: 2023-07-12T13:37:00.000Z
description: This blog post shares the author's journey in mitigating the frustrating issue of code rot in his technical projects. He introduces the practical strategy of hardcoding the versions of project dependencies, offering a simple process for this and demonstrating its execution.
tag: web development
author: Isaac
---


So i decided not too long ago that I wanted to give a good solid go at the technical blogging. I've had a couple different small little blogs, they were mostly just practicing different platforms and seeing what I liked. However, I usually run into the problem of my projects rotting when i come back to them in 5-6 months. 

There's a dark truth to programming with modern web components, if you leave a project for any significant amount of time (+3 months) there's a good chance that your project won't run again and you'll be left with vague unhelpful error messages. You can update packages, or even go backward and have no luck. Sure you can figure it out, but honestly for small little projects like what my blogs have been, I've never cared to do so. I have now had to resurrect my blog about 3-4 times. This time though, I'm going to do something different to hopefully mitigate this issue. 

This time around as i was swearing to myself trying to figure out a new solution for my blog, i swore that I would set in stone the versions of dependancies i was using and commit it to my repo. This way if i came back to the project in 6 months or a year later, and I should 🤞 be able to get things running without having to fiddle around with any dumb dependency versions. 

The process is really quite straight forward, whether your working in Javascript, or python, or golang, this is a good practice. You can choose to set your versions in a way that suits your style. If you are active on a project and keeping up with things, goa head and choose to wildcard your versions. But on the other hand, if you just don't want ot think about it again and don't care about incremental upgrades, you can set explicitly the version numbers and they will never change. 

Of course you can still manually update as you go along, but that is something you can choose to do, instead of running into situations where you just have to because things don't work anymore 🤦. 

## Process

So for my blog my process is going to look something like this. 

1. Sanity check
	1. Going to run the app and make sure that things work of course. It's been only a few days, but you never know. 
2. Upgrade packages using npm
	1. This will ensure things are updated as much as possible at this time
3. Test again things work
	1. After making those changes, it's always good to ensure you haven't broken anything... again
4. Commit the exact version numbers to the repo. 

I will have to look it up, but i suppose npm has a way to get the exact versions that you are running. I know pip has this in the python world, i will use chat gpt or copilot to find the similar command for javascript. 

## Begin

So it turns out i was using yarn as my main package manager, so i'll go forward using that. I wanted to start by upgrading things, i did that using:

`yarn upgrade`

Now the nice thing about version control, is that if anything is changed systematically, I will know about it because my tools will show me the updates. 

This time around, when i did my upgrade I did not have any major updates. I recently forked this project so things are still up to date. Never lasts very long, but so far so good. 

Ok and with a little help from Github's copilot, here's a cool command that should set the versions exactly:

`yarn upgrade --exact --latest`

Well this command set some of the dependancies like I wanted, but only about half of them... I guess the saving grace is that it does list out your direct dependancies and the versions they are running, so with a little manual work they can be hard set. 

Ok now that I have hard coded all the versions, i'm going to reinstall the dependancies after deleting the lock files, and then running a build and running it again to ensure everything is going smoothly. 

## Conclusion

Well there we have it, a small effort that I hope will go a long way in slowing down the inevitable rotting of code. Here's my commit message, feels good to finally address this issue instead of just procrastinating for months:

"hard coding dependency versions to slow code rot"

For reference, here's the package.json:

```json
{
  "private": true,
  "license": "MIT",
  "scripts": {
    "dev": "next",
    "build": "node ./scripts/gen-rss.js && next build",
    "start": "next start"
  },
  "dependencies": {
    "@vercel/analytics": "1.0.1",
    "gray-matter": "4.0.3",
    "next": "13.4.9",
    "nextra": "2.9.0",
    "nextra-theme-blog": "2.9.0",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "rss": "1.2.2"
  },
  "prettier": {
    "arrowParens": "always",
    "singleQuote": true,
    "tabWidth": 2,
    "trailingComma": "none",
    "semi": false
  }
}
```
