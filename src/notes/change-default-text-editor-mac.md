---
title: Changing the default text editor on macOS
date: 2022-01-19
link: https://apple.stackexchange.com/questions/123833/replace-text-edit-as-the-default-text-editor/123834#123834
---

The command line trick works for all text files across the whole system, including hidden files, and I never have to think about it again

```sh
# VS Code
defaults write com.apple.LaunchServices/com.apple.launchservices.secure LSHandlers -array-add '{LSHandlerContentType=public.plain-text;LSHandlerRoleAll=com.microsoft.VSCode;}'

# Sublime Text 4
defaults write com.apple.LaunchServices/com.apple.launchservices.secure LSHandlers -array-add '{LSHandlerContentType=public.plain-text;LSHandlerRoleAll=com.sublimetext.4;}'

# Sublime Text 3
defaults write com.apple.LaunchServices/com.apple.launchservices.secure LSHandlers -array-add '{LSHandlerContentType=public.plain-text;LSHandlerRoleAll=com.sublimetext.3;}'
```
