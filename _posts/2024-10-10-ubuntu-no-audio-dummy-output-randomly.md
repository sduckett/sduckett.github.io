---
layout: post
title: Framework13, Ubuntu, and the Case of the Missing Audio
---

## The Problem
After _n_ hours of using the laptop's audio device, probably after a
lid-shut event, we login and notice there is no real audio device, only
a _Dummy Output_ device. What changed, when I haven't changed system
software?

## The Fix
This works on my machine, with a fresh install of Ubuntu 24.04.1 LTS:

- add `snd-intel-dspcfg.dsp_driver=1` to `/etc/modprobe.d/alsa-base.conf`
- add `blacklist snd_soc_skl` to `/etc/modprobe.d/blacklist.conf`
- reboot

Note: on older kernels, and in many forum posts, the `alsa-base`
addition was `#options snd-hda-intel dmic_detect=1`.

## References
Finding the set of modprobe additions took a bit of duck-ducking, but I
got there in the end.

- https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061
- https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html
