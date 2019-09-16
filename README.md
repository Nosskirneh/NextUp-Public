# NextUp-Public

[NextUp](https://henrikssonbrothers.com/cydia/repo/depictions/?p=se.nosskirneh.nextup2) is a nice little enhancement that allows you to glimpse ahead of the current track and even change it if you don't like the what the future had in store for you.

Don’t like a song? Skip it before it has even started playing.

It’s especially useful for those of you using free accounts with limited number of skips.

It has support for a lot of media apps (the ones currently supported: VOX, Musi, Music, TIDAL, Spotify, Deezer, Napster, Anghami, JioSaavn, Podcasts, SoundCloud, Google Music and YouTube Music).

<div>
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup1.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup2.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup3.jpg" width="200">
    <img src="http://moreinfo.thebigboss.org/moreinfo/nextup5.jpg" width="200">
</div>

## Translate NextUp

It was a requested feature to have translations of the "Next Up" label.

Do you know a language that NextUp isn't translated to yet and want to help? First make sure that the language is not already translated and uploaded [here](https://github.com/Nosskirneh/NextUp-Public/blob/master/translations). Refer to the [English translation]([API.md](https://github.com/Nosskirneh/NextUp-Public/blob/master/translations/en.lproj)) within this repo. Copy its folder, change its name to your [country's code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) (see column 639-1) and translate the `Localizable.strings` file. Zip it and send me the zip somehow (email visible from Cydia for example) or open a pull request to this repo.

## Issues

### Troubleshooting / FAQ

Down below I’ll be listing a few frequently support emails I get. I spend a lot of time answering support emails. I would appreciate very much if you could read through this short list before emailing me. That way I can spend more time actually improving my tweaks.

#### It complains about RocketBootstrap > 1.0.6, please help!
Add [Ryan Petrich's repo](https://rpetri.ch/repo/) and install the latest version of RBS which is compatible with iOS 12.

#### My license won’t activate, please help!
* Make sure you’re pressing the correct choice when it asks if you bought NextUp for iOS 11.
* Make sure you spelled your email correctly (sometimes users have several emails – even if you think you know which one PayPal used, verify it).

#### My device crashes when I begin playing music, please help!
Seems like you’re using the iOS 11 version of NextUp on iOS 12. Please install the correct version from https://henrikssonbrothers.com/cydia/repo.

#### My device crashes when entering the lockscreen playing music, please help!
Seems like you installed an old version of NextUp from a “piracy” repo that is incompatible with iOS 12.2 and above. Please add https://henrikssonbrothers.com/cydia/repo and install the latest version.

#### My device crashes and I checked all the above:
Okay, please use iCleaner Pro to disable all your other tweaks. Does it work? If it does, enable chunks of 1/2 until it crashes again to find out which tweak is incompatible. Still not working? Please email me or open an issue here. Attach a crash log (through CrashReporter).

#### NextUp isn’t working, nothing appears.
This could be caused by a few reasons:
    * make sure you’re running 1.0.7 of RocketBootstrap from tpetrich repo. Sometimes RBS stops working. Try reinstalling and respringing.
    * Make sure you’re not having a code injection blocker such as UnSub enabled for the media app.


### Report an issue

Please include the following when reporting a bug:

1. What app or process isn't working.
2. App version (if applicable) and iOS version.
3. How to reproduce (if not obvious steps).

Also please make sure the bug isn't caused by another tweak (disable all other just to make sure).

## Support for new clients
See [API.md](https://github.com/Nosskirneh/NextUp-Public/blob/master/API.md) if you're a developer.
