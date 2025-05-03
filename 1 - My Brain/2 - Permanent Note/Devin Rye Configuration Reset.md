---
created: 2025-04-27
tags: [troubleshooting, rye, devin, python]
description: How to fix Rye PATH issues after Devin shell session restart
reference: https://g.co/gemini/share/d4d0420a0a02
---
# Troubleshooting Note

## Issue:
* Rye installed during "4. Maintain Dependencies" in Devin setup is not being recognized
* The `rye` command becomes unavailable after shell restart

## Cause:
* Devin restarts the shell session as part of its operation
* Since Rye's PATH is not written in .bashrc, the PATH configuration is lost when the shell session restarts
* This is a common issue with shell-based tools that modify PATH temporarily

## Resolution:
* Add Rye to bashrc permanently:
	* `echo 'export PATH="$HOME/.rye/shims:$PATH"' >> ~/.bashrc`
	* `source ~/.bashrc`

## Verification:
* After applying the fix, you can verify it works by:
	1. Opening a new terminal
	2. Running `rye --version` to confirm Rye is accessible
	3. Running `which rye` to verify the correct shims path is being used
