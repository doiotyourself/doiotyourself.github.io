---
layout: post
title: VSCodium Extensions
---

A short post today to talk about a few VSCodium Extensions that increase my productivity. 

1. yzhang.markdown-all-in-one
2. mushan.vscode-paste-image
3. ban.spellright
4. DavidAnson.vscode-markdownlint


## Markdown all in one 

All you need for Markdown (keyboard shortcuts, table of contents, auto preview and more).

## Paste Image

Paste image directly from clipboard to markdown.

Needs xclip which can be installed through Muon package manager

Keyboard shortcut `Ctrl+Alt+v`

Config for this jekyll site (saved in `.vscode/settings.json`):

{% highlight json%}
{
    "pasteImage.basePath": "${currentFileDir}",
    "pasteImage.namePrefix": "doiotyourself.com_${currentFileNameWithoutExt}_",
    "pasteImage.path": "${projectRoot}/images",
    "pasteImage.forceUnixStyleSeparator": true,
    "pasteImage.prefix": "/",
    "pasteImage.filePathConfirmInputBoxMode": "onlyName",
    "pasteImage.showFilePathConfirmInputBox": true
}
{% endhighlight %}

![Image by <a href="https://pixabay.com/users/geralt-9301/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1927697">Gerd Altmann</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1927697">Pixabay</a>](/../images/doiotyourself.com_2023-01-26-VSCodium-Extensions_IoT-hand.png)

## Spell Right

Multilingual, Offline and Lightweight Spellchecker

{% highlight terminal%}
ln -s /usr/share/hunspell/* ~/.config/VSCodium/Dictionaries
{% endhighlight %}

Codium command `SpellRight: Select Dictionary (Language)`

## markdownlint

markdownlint includes a library of rules to encourage standards and consistency for Markdown files.
