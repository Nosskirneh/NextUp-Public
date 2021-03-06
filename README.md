# NextUp-Public

NextUp ([iOS 12 & 13](https://henrikssonbrothers.com/cydia/repo/depictions/?p=se.nosskirneh.nextup2) and [iOS 11](http://cydia.saurik.com/package/se.nosskirneh.nextup/) versions) is a nice little enhancement that allows you to glimpse ahead of the current track and even change it if you don't like the what the future had in store for you.

Don’t like a song? Skip it before it has even started playing.

It’s especially useful for those of you using free accounts with limited number of skips.

It has support for a lot of media apps (the ones currently supported: VOX, Musi, Music, TIDAL, Spotify, Deezer, Napster, Anghami, JioSaavn, Podcasts, AudioMack, SoundCloud, Google Music and YouTube Music).

<div>
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup1.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup2.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup3.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup5.jpg" width="200">
</div>

## Translate NextUp

It was a requested feature to have translations of the "Next Up" label.

Do you know a language that NextUp isn't translated to yet and want to help? First make sure that the language is not already translated and uploaded [here](https://github.com/Nosskirneh/NextUp-Public/blob/master/translations). Refer to the [English translation]([API.md](https://github.com/Nosskirneh/NextUp-Public/blob/master/translations/en.lproj)) within this repo. Copy its folder, change its name to your [country's code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) (see column 639-1) and translate the `Localizable.strings` file. Zip it and send me the zip somehow (email adress can be found from within Cydia for example) or open a pull request to this repo.

## Issues

### Troubleshooting / FAQ

Down below I’ll be listing a few frequently support emails I get. I spend a lot of time answering support emails. I would appreciate very much if you could read through this short list before emailing me. That way I can spend more time actually improving my tweaks.

#### My license won’t activate, please help!
* Make sure you’re pressing the correct choice when it asks if you bought NextUp for iOS 11.
* Make sure you spelled your email correctly (sometimes users have several emails – even if you think you know which one PayPal used, verify it).

#### My device crashes after installing NextUp:
Okay, please use iCleaner Pro to disable all your other tweaks. Does it work? If it does, enable 1/2 and try again. Issue becomes present again? Disable 1/2 of the 1/2 you just enabled. Rinse and repeat until you find which tweak is in incompatible. Still not working? Please email me or open an issue here. Attach a crash log (through CrashReporter).

#### NextUp isn’t working, nothing appears.
This could be caused by a few reasons:
* Make sure you’re running 1.0.7 of RocketBootstrap from BigBoss. Sometimes RocketBootstrap randomly stops working and won't start again. Try reinstalling it and respring.
* Make sure you’re not having a code injection blocker, such as UnSub or Liberty Lite, enabled for the media app.
* If the two bullet points above do not work for you, it might be a conflicting tweak. Use the method from the FAQ question above to solve that.


### Report an issue

Please include the following when reporting a bug:

1. What app or process isn't working.
2. App version (if applicable), iOS version and NextUp version.
3. How to reproduce (if not obvious steps).
4. Crash report if such exists.

Also please make sure the bug isn't caused by another tweak (disable all other just to make sure).

## Support for new clients
See [API.md](https://github.com/Nosskirneh/NextUp-Public/blob/master/API.md) if you're a developer.
