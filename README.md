# macOS-tips-tricks
Just a list of commands and settings for whenever I do a fresh macOS installation, as well as fixes for common annoyances

## Privacy

A few are taken from the macOS-Security-and-Privacy-Guide:

Disable Spotlight Bing Search Suggestions in System Preferences, as well as Safari Suggestions in Safari Preferences.

Disable opening "Safe" files in Safari.

Enable the Develop menu safari( useful for opening pages in Chrome, go to Develop-> Open Page With)

Enable Secure Keyboard Entry in Terminal.

Disable loading Remote Images in Mail

Disable Captive Portal:
```
sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.captive.control Active -bool false
```
## Display
Text Smoothing: Halfway in between subpixel antialiasing and greyscale antialiasing.
defaults -currentHost write -globalDomain AppleFontSmoothing -int 2

Disable Ambient Display: (http://www.mackungfu.org/el-capitan-s-crazy-gamma-adjustments-photographers-beware)

```
cd /System/Library/PrivateFrameworks/AmbientDisplay.framework/Versions/A/XPCServices/com.apple.AmbientDisplayAgent.xpc/Contents/MacOS/

sudo mv com.apple.AmbientDisplayAgent _com.apple.AmbientDisplayAgent
```
Enable HiDPI resolutions:
```
sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```

## Behaviour

Change Key repeat	to fast in System Preferences

Disable the Rotate gesture for the Trackpad in System Preferences

Show Hidden Files:
```
defaults write com.apple.finder AppleShowAllFiles YES
```

Globally disable auto-saving Documents to iCloud:
```
defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false
```

TextEdit Old Behaviour, starts by showing empty text file:
```
defaults write com.apple.TextEdit NSShowAppCentricOpenPanelInsteadOfUntitledFile -bool false
```

Power Chime whenever your Power Supply is plugged in:
```
defaults write com.apple.PowerChime ChimeOnAllHardware -bool true;open /System/Library/CoreServices/PowerChime.app &
```

Stop Photos from opening every time you connect something with images:
```
defaults -currentHost write com.apple.ImageCapture disableHotPlug -bool NO
```
Disable automatic iDevice sync:
Go to iTunes and check `Prevent iPods, iPhones, and iPads from syncing automatically`

## Fixes

Disconnect from a broken SSH Connection:
`Enter` + `~` + `.`

Flush DNS Cache
```
sudo dscacheutil -flushcache;sudo killall -HUP mDNSResponder
```
Append Search Domain
```
sudo launchctl unload /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo defaults write /Library/Preferences/com.apple.mDNSResponder.plist AlwaysAppendSearchDomains -bool YES
sudo launchctl load /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
```

Fix Launchpad
```
defaults write com.apple.dock springboard-columns -int 6;defaults write com.apple.dock springboard-rows -int 4;defaults write com.apple.dock ResetLaunchPad -bool TRUE;killall Dock
```

Allow Apps from Any Developers
```
sudo spctl --master-disable
```

Install App with Outdated xattr:
```
xattr -c /path/to/app.app
```

## Finder

Show all extensions:
```
defaults write NSGlobalDomain AppleShowAllExtensions -bool true
```
Get rid of Remote Disc
```
sudo defaults write /Library/Preferences/com.apple.NetworkBrowser EnableODiskBrowsing -bool false
```
Show Library in Home Folder:
Click Home folder, then the View Options dialog box, select Show Library Folder.	


## Software

Install brew from http://brew.sh

Install borgbackup from brew

If you have a mouse with side buttons, install Sensible Side Buttons
