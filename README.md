# Cody for Offline Visual Studio Code (VSC) Autocomplete: A 3-Step Quickstart (For FREE and PRO accounts)

## Read This First 👋 
- I'm just a Cody fanboy. **I have NO affiliation with Sourcegraph**:
  -  https://twitter.com/rory_blyth/
  - https://mastodon.social/@rory_blyth
- The linked article is missing a key configuration setting. Don't worry. It's in this guide.

- I created this streamlined step-by-step guide based on the full Sourcegraph post here: https://sourcegraph.com/blog/local-code-completion-with-ollama-and-cody. (THANK YOU, ADO! https://ado.xyz)

- If you're comfortable with Visual Studio Code (VSC), this should take you about ten minutes. Most of that is waiting for the LLM to download.

### 🛑 Before you proceed...
- Make sure you have the VSC Cody extension installed (FREE account tier is supported!): https://sourcegraph.com/cody
- Using even a small local language model can chew up RAM (and battery if you're on a laptop). I run an M1 with 64GB RAM, and Ollama does brilliantly. YMMV.

- Cody uses the local LLM for code-completion AND chat. You can use VSC + Cody + Ollama as a completely free, completely airgapped chat and autocomplete solution. **No internet required.** Cody does all the things. And you can use many models. Not just codellama!

## Step 1: Get Ollama and the LLM
### You'll need ~5GB drive space for the application and LLM:
1. Download and install Ollama: https://ollama.com

2. Open terminal \(command line\)

3. Paste: `ollama run codellama` (then press Enter)

Wait a few minutes as Ollama downloads and mounts the LLM for you (it will save the model file for future use).

## Step 2: Modify VSC's User Settings

1. Open Visual Studio Code (VSC)

2. Open the Command Palette (Ctrl+Shift+P on Windows/Linux, Cmd+Shift+P on Mac)

3. Paste this into the Palette field: `user settings json`

4. Select "Preferences: Open User Settings (JSON)"

### Add this snippet to the end of the file (before the final closing curly brace "}"):
```
"cody.autocomplete.advanced.provider": "experimental-ollama",
"cody.autocomplete.experimental.ollamaOptions": {
  "url": "http://localhost:11434",
  "model": "codellama"
},
"cody.experimental.ollamaChat": true
```
**The bottom of your config file should look like this (note the leading comma!):**
```
  ,
  "cody.autocomplete.advanced.provider": "experimental-ollama",
  "cody.autocomplete.experimental.ollamaOptions": {
    "url": "http://localhost:11434",
    "model": "codellama"
  },
  "cody.experimental.ollamaChat": true
}
```
**Now save the config file (Ctrl+S on Windows/Linux, Cmd+S on Mac), close its tab, and carry on!**

## Step 3: Test!
### Optional: Disable WiFi (oh, no!)
- Disable WiFi: This way you'll know Cody is using the local provider.

### New Chat:
1. Click on the Cody extension (the winking smiley face), select "New Chat," and go to town. But **remember to select your new local LLM from the dropdown**. If you followed these steps to the letter, you should see "Codellama:latest" as an option (you might have to scroll down to find it).

2. If you found your model in the list, type something like "Hi. You there?" then press Enter. If Cody answers, well, *chat*! If you get an error, **double-check your json settings** (if you're on macOS and *really* frustrated, DM me and I'll help you out: https://twitter.com/rory_blyth/).

### Autocomplete:
1. Create a new file in VSC (for the language of your choice)

2. Code! You should see autocompletion suggestions from the local Ollama hosted LLM as you type. You know. The way autocomplete works.

#
### My Thoughts on Local GPT (as of 2024-04-26):
- If you have the hardware, if you lack a net connection, and if you really need local GPT based autocomplete, this is a solution.

- Paying $9/mo for a Cody Pro subscription is far cheaper up front (you don't have to buy a supercomputer), and it comes with **unlimited Claude Opus 3, GPT-4 Turbo, Mistral, etc.** Unlimited chat windows open side-by-side so you can see which LLM works the best for you \(it'll probably be **Claude 3 Opus/Sonnet** for most users\).

- Local GPT is fun. It'll get better. For now, tools like Cody Pro are probably the better option and will save you a *lot* of hassle.
#
### The Missing Piece
If you have a problem (such as something not working because of a missing line from a blog post), head over here: https://community.sourcegraph.com/c/cody
