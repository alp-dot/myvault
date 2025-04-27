---
created: 
tags: 
description: 
reference: https://g.co/gemini/share/d4d0420a0a02
---
# Troubleshooting Note

## Issue:
* Rye installed during "4. Maintain Dependencies" in Devin setup is not being recognized

## Cause:
* Devin restarts the shell session
* Since it's not written in .bashrc, the Rye PATH is lost when the shell session restarts

## Resolution:
* Add to bashrc:
	* `echo 'export PATH="$HOME/.rye/shims:$PATH"' >> ~/.bashrc`
	* `source ~/.bashrc`
