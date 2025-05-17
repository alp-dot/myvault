---
created: 2025-05-17
tags:
  - nodejs
  - npm
description: 
reference:
---
# Guide to Setting Up Node.js Environment on Mac (nvm + npm)

## 1. Technology Choice Rationale

### Why Node Version Manager (nvm)?

- **Multiple Version Management**: Easily install and switch between different Node.js versions for different projects. This facilitates both maintaining legacy projects and testing new versions.
- **Clean Global Environment**: Prevents system-wide conflicts by managing Node.js and related tools under nvm instead of installing them globally.
- **Project-Specific Versioning**: Share and standardize Node.js versions across your team by placing a `.nvmrc` file in the project root.

### Why Node Package Manager (npm)?

- **Built into Node.js**: Comes bundled with Node.js installation, allowing immediate use without additional setup.
- **Vast Ecosystem**: Access to the world's largest software registry with an abundance of available packages.
- **Low Learning Curve**: Best to start with the standard npm when beginning with Node.js, with the option to explore alternatives like Yarn or pnpm later. npm is sufficient for most initial needs.

## 2. Initial nvm Setup Guide (macOS, Zsh shell)

Follow these steps to install nvm via Homebrew and configure it in Zsh shell.

### Step 1: Install nvm via Homebrew

Open your terminal and run the following command.
(If Homebrew isn't installed, first follow the installation instructions on the Homebrew official website.)

```bash
brew install nvm
```

### Step 2: Configure nvm in ~/.zshrc

Add nvm configuration to load automatically when starting a shell session.

First, open ~/.zshrc in your editor:
```bash
nano ~/.zshrc
```

Add these lines at the end of the file. This is the standard configuration for Homebrew-installed nvm:
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$(brew --prefix nvm)/nvm.sh" ] && \. "$(brew --prefix nvm)/nvm.sh"  # This loads nvm
[ -s "$(brew --prefix nvm)/etc/bash_completion.d/nvm" ] && \. "$(brew --prefix nvm)/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

Save and close the file (in nano: Ctrl + O to save, Ctrl + X to exit).

### Step 3: Apply the Configuration

Apply the settings to your current terminal session by running:
```bash
source ~/.zshrc
```

Alternatively, open a new terminal window/tab.

### Step 4: Verify nvm Installation

Confirm that nvm is properly configured:
```bash
command -v nvm
```

You should see `nvm` displayed.

Check the nvm version:
```bash
nvm --version
```

If you see a version number, nvm setup is complete.

### Step 5: Install Node.js and Set Default Version

For example, let's install the LTS (Long Term Support) version and set it as the default:

Install Node.js (lts):
```bash
nvm install --lts
```

(Note: While newer LTS versions exist, v18 (Hydrogen) is the default version in this region. You can still install other versions if needed using specific version numbers or LTS aliases.)

Set the default version:
To make lts the default version when opening new terminals:
```bash
nvm alias default lts
```

This completes the basic setup of a Node.js development environment using nvm and npm on macOS.
You can now switch Node.js versions for each project using `nvm use <version>` or by creating a `.nvmrc` file in your project directory.
