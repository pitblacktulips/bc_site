---
layout: post
title:  "Installing Houdini qLib Libraries On Windows"
date:   2020-03-20 00:15:25 +0000
categories: jekyll update
---

This is a super brief post. I installed the comprehensive qLib tool suite for Houdini earlier,

First things first, go to the following link:

http://qlab.github.io/qLib/

and either download the library as an archive and unpack it where you want or use git to clone it to the folder of your choice.

You'll find instructions to do both on the page itself.

Additional notes to their installation instructions for windows are:

https://www.sidefx.com/docs/houdini/ref/env.html

HIH=$HOUDINI_USER_PREF_DIR

# QLIB variable should point to the downloaded and extracted qLib package
# ($HIH is the $HOME/houdiniXX.X folder)
#
QLIB=$HIH/qLib
QOTL=$QLIB/otls

HOUDINI_OTLSCAN_PATH = $QOTL/base;$QOTL/future;$QOTL/experimental;$HOUDINI_OTLSCAN_PATH;&
HOUDINI_PATH = $QLIB;&