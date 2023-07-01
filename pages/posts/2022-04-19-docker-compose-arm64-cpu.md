---
title: Docker-Compose on Arm64 CPU instance
date: 2022-04-19T13:37:00.000Z
description: Installing docker-compose on my arm64 cpu instance required a little extra work, and a beta release.
tag: web development
author: Isaac
---

Installing docker-compose on my arm64 cpu instance required a little extra work, and a beta release.

Following the instructions on docker docs didnt work for arm64. i had to use a beta release for docker compose v2, i got it here

https://github.com/docker/compose-cli/releases/tag/v2.0.0-beta.3

So something like:

`curl -o https://github.com/docker/compose-cli/releases/tag/v2.0.0-beta.3 ./`

I needed to first remove the file from my first failed attempt:

`sudo rm /usr/local/bin/docker-compose`

Then copy and rename the beta file to it's final resting place: (as per docs)

`sudo cp ./docker-compose-linux-arm64 /usr/local/bin/docker-compose`

give it executable permissions (as per docs)

`sudo chmod +x /usr/local/bin/docker-compose`

Finally, when using the newly installed docker-compose, I had to use an extra `compose` command I'm not used to:

`sudo docker-compose compose up --build`

And there it works.  little extra work but its going strong!
