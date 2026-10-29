# useful-terminal-command

macOS terminal cheatsheet. Each command was run on macOS 26.6 (zsh) when added.

## Clipboard and files
```sh
pbcopy < file.txt              # file -> clipboard
pbpaste > out.txt              # clipboard -> file
open -R path/to/file           # reveal in Finder
mdfind -name "report" -onlyin ~/Documents   # Spotlight search by file name
du -hd1 . | sort -h            # size of each subdirectory, largest last
```

## Images
```sh
sips -g pixelWidth -g pixelHeight photo.heic   # read dimensions
```
Duplicate JPG/HEIC pairs: see [image-process.md](image-process.md).

## System
```sh
sw_vers -productVersion                      # macOS version
pmset -g batt                                # battery / power source
caffeinate -t 3600                           # keep awake for 1 hour
defaults read NSGlobalDomain AppleInterfaceStyle   # prints "Dark" in dark mode; errors in light mode
diskutil list                                # disks and partitions
```

## Network
```sh
lsof -nP -iTCP -sTCP:LISTEN    # processes listening on TCP ports
networksetup -listallhardwareports   # interface names (en0, ...)
```
