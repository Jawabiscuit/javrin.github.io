---
draft: false
title: Tame Multiple Obsidian Vaults With This Plugin Sync Hack
date: 2024-04-20T10:57:56-04:00
created: 2024-04-20 10:57
modified: 2024-04-20 13:02
categories:
  - Productivity
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
tags:
  - obsidian
  - bash
  - snippet
---

&nbsp;

If you're like me and you've tried to maintain multiple Obsidian vaults, odds are you've encountered the same headache of having to sync plugins and settings which usually takes you out of the flow. You also might be thinking to yourself, why haven't I done something about this yet, I mean, I love hacking in the terminal don't I?

&nbsp;

I separate vaults based on a variety of reasons, but a common reason would be to separate your public and private notes. This is beneficial for organization, but creates more busy work if you like keeping your plugins and settings in sync. Now that my vault count has now grown beyond 3, I finally broke down and scripted the synchronization process for multiple vaults. Whether you juggle personal and work vaults or maintain multiple knowledge bases, these snippets are must-have productivity hacks.

&nbsp;

> Spice Rating: 🌶🌶🌶 -
>
> This guide covers using bash scripts to synchronize Obsidian plugin settings across multiple vaults. Familiarity with Obsidian's plugin folder structure and prior experience using bash terminals is assumed. Running code from the internet can be destructive so always test and make backups of your files before hand!

Also note I'm writing this on a Windows machine but should work for any platform since you can run bash on all of them. Why don't I use git? I do, but I don't like tracking plugin settings which could have sensitive information like API keys 😱!

&nbsp;

# Sync Obsidian Plugin Settings (single vault)

If you haven't been scared away, I will briefly break down how the first simple one-liner works. There are 2 versions of each snippet, dry run and execute, for both single and multi-vault variants. You'll want to use the single vault variant if the number of vaults you have is currently manageable or feel more comfortable running just one line of code.

&nbsp;

The "Dry Run" command uses the `find` utility to locate all `data.json` files within the `.obsidian/plugins/` directory of your current vault. **Note that you'll need to `cd` to your current vault first**. This is where Obsidian stores plugin settings and data. The `-print` option just prints the full paths of the matched files to the console, allowing you to preview what would be copied without actually copying anything yet.

&nbsp;

The "Execute" command is similar, but instead of just printing the paths, it uses the `-exec` option to run the `cp` command on each matched file. This copies the `data.json` file to the `/p/obsidian/personal-notes/` directory while preserving the same nested folder structure under `.obsidian/plugins/`. So in effect, running this second command line will sync all your current vault's plugin settings over to a second vault located at `/p/obsidian/personal-notes/`.

&nbsp;

> Dry Run (print only)
>
> `find .obsidian/plugins/ -type f -name data.json -print`
>
> Execute (copy)
>
> `find .obsidian/plugins/ -type f -name data.json -exec cp {} /p/obsidian/personal-notes/{} \;`

&nbsp;

# Sync Obsidian Plugin Settings (multiple vaults)

This variant extends previous single vault script to handle multiple destinations.

&nbsp;

Similar to the single vault variant, the "Dry Run" version of the script just prints out the `cp` operations it would perform without actually copying anything. This lets you validate the output before executing the real copy.

&nbsp;

> Dry run (print only)
>
> ```bash
> find .obsidian/plugins/ -type f -name data.json -exec sh -c '
> src="$1"
> dir=$(dirname "$src")
> for dest in /p/obsidian/business-vault /p/obsidian/personal-notes /p/obsidian/mysite.github.io /p/obsidian/obsidian-notes; do
> echo cp -uv "$src" "$dest/$dir"
> done' _ {} \;
> ```
>
> Execute (copy)
>
> ```bash
> find .obsidian/plugins/ -type f -name data.json -exec sh -c '
> src="$1"
> dir=$(dirname "$src")
> for dest in /p/obsidian/business-vault /p/obsidian/personal-notes /p/obsidian/javrin.github.io /p/obsidian/obsidian-notes; do
> cp -uv "$src" "$dest/$dir"
> done' _ {} \;
> ```

&nbsp;

Here's a breakdown of what's happening:

1. `find` is used again to locate all `data.json` files in the current vault's `.obsidian/plugins/` folder.
2. For each match, it runs the code in the `-exec sh -c` block, passing the full path as `$1`.
3. It stores the source file path in `$src` and gets just the directory path in `$dir`.
4. Then it loops over the list of destination vault paths defined in the `for dest in …` line.
5. For each destination, it runs `cp -uv "$src" "$dest/$dir"` to copy the source file to the same nested folder structure within that vault.
6. The `-u` option updates only when the source is newer than the destination.
7. The `-v` option makes it print the file paths as it copies.

&nbsp;

So with this one command, you can sync your plugin settings to as many vaults as needed by just adding/removing paths in the `for dest in …` line. Odds are, your paths are different so you'll need to remove them from the example before running, but you knew that already 😉.

&nbsp;

With that, you now have a powerful way to streamline managing plugins across all your Obsidian vaults. Let me know if it makes your life a little less tedious! If it's your first foray into the world of using terminal for productivity hacks in general or for Obsidian I'd definitely like to hear how your experience went with implementing what was discussed here.
