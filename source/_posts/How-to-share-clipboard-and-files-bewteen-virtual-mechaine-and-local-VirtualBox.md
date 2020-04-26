---
title: >-
  How to share clipboard and files bewteen virtual mechaine and local -
  VirtualBox
date: 2020-04-26 09:54:03
categories: engineer
tags:
- VirtualBox
- environment
---

## Enable Shared Clipboard and Drag 'n' Drop in setting

1. Select the virtual machine you want to set in VirtualBox

2. Click Settings on the top

3. General -> Advanced

   ```
   Shared Clipboard : Bidirectional/ Guest to Host/ Host to Guest (based on your need)
   Drag 'n' Drop : Bidirectional/ Guest to Host/ Host to Guest (based on your need)
   ```

## Start virtual machine

1. Try the shared clipboard and Drag&Drop (which allows you to drag files between loacl and virtual machine)
2. If it works, congratulations!
3. If not and the virtual machine runs with Linux system (Ubuntu, Mint, etc.), see the following step

## Install Additions

1. Start the virtual machine if it is not already running.
2. Devices -> Insert Guest additions
3. In virtual machine, follow the steps showed on the screen, for example, in Mint, just click 'OK'.
4. Restart the virtual machine as requires.
5. After restarting, you should be able to use shared clipboard and drag 'n' drop.