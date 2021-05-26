# Disable autocomplete in Kali linux

Source: https://www.reddit.com/r/linuxquestions/comments/kceayq/disable_command_history_autocomplete_suggestions/gqpe1cz?utm_source=share&utm_medium=web2x&context=3

1. Run the following command
```
nano .zshrc
```
2. Locate `enable auto-suggestions based on the history` section
```
# enable auto-suggestions based on the history
if [ -f /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh ]; then
    . /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh
    # change suggestion color
    ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=#999'
fi
```
3. Comment out the code
```
# enable auto-suggestions based on the history
#if [ -f /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh ]; then
#    . /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh
#    # change suggestion color
#    ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=#999'
#fi
```
4. Close and reopen the terminal
