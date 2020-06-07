# NextUp's API
*Requires NextUp version 1.0.1 or later.*

Prerequisites: [RocketBootstrap](https://github.com/rpetrich/RocketBootstrap/tree/master) and [AppSupport](http://developer.limneos.net/?ios=11.0&framework=AppSupport.framework&header=CPDistributedMessagingCenter.h) headers.

If you’re running iOS 12 or above, make sure to have RocketBootstrap version 1.0.7 or higher.

Other developers can easily support their favorite media clients. You'll need to find the class that manages the queue and hook methods that are called when the next track is changed. Once you have that, you'll need to find the class that fetches images and fetch the next track's image using it. This method is most usually a callback method that returns an `UIImage`.

## The Makefile
RocketBootstrap requires the Makefile to specify the rocketbootstrap library and the AppSupport framework.
```
TweakName_LIBRARIES = rocketbootstrap
TweakName_PRIVATE_FRAMEWORKS = AppSupport
```

## Communication
There are two different messages transferred to NextUp:

|               name               |                     description                     |
|----------------------------------|-----------------------------------------------------|
`se.nosskirneh.nextup/registerApp` | Registers the app to be able to send data to NextUp |
`se.nosskirneh.nextup/nextTrack`   | Sends the next available track                      |


When the callback with the `UIImage` fires, refer to the code below to communicate with NextUp's SpringBoard listener.

```
#import <AppSupport/CPDistributedMessagingCenter.h>
#import <rocketbootstrap/rocketbootstrap.h>

#define NEXTUP_IDENTIFIER @"se.nosskirneh.nextup"
#define kApp @"app"
#define kMetadata @"metadata"
#define kRegisterApp @"se.nosskirneh.nextup/registerApp"
#define kNextTrackMessage @"se.nosskirneh.nextup/nextTrack"


void sendNextTrackMetadata(NSDictionary *metadata) {
    CPDistributedMessagingCenter *c = [%c(CPDistributedMessagingCenter) centerNamed:NEXTUP_IDENTIFIER];
    rocketbootstrap_distributedmessagingcenter_apply(c);

    NSMutableDictionary *dict = [NSMutableDictionary new];
    dict[kApp] = [[NSBundle mainBundle] bundleIdentifier];

    if (metadata)
        dict[kMetadata] = metadata;
    [c sendMessageName:kNextTrackMessage userInfo:dict];
}

void registerApp() {
    CPDistributedMessagingCenter *c = [%c(CPDistributedMessagingCenter) centerNamed:NEXTUP_IDENTIFIER];
    rocketbootstrap_distributedmessagingcenter_apply(c);

    [c sendMessageName:kRegisterApp userInfo:@{
        kApp: [[NSBundle mainBundle] bundleIdentifier]
    }];
}

%hook SomeClass

- (void)someMethod {
    %orig;
}

%end

%ctor {
    registerApp();
}
```

## Data structure
Along with each message, some data is also sent.

### Register app message
The data is built with a `NSDictionary` in the following way:

|   key    |    type    |         description         |
|----------|------------|-----------------------------|
| `app`    | `NSString` | The app's bundle identifier |

### Next track message
The data is built with a `NSDictionary` in the following way:

|    key     |   type         |          description         |
|------------|----------------|------------------------------|
| `app`      | `NSString`     | The app's bundle identifier. |
| `metadata` | `NSDictionary` | Info about the next track.   |


The `metadata` dictionary is built in the following way:

|    key     |   type     |          description          |
|------------|------------|-------------------------------|
| `title`    | `NSString` | The text on the first label.  |
| `subtitle` | `NSString` | The text on the second label. |
| `skipable` | `NSNumber` | If the next track is skipable or not (optional and defaults to `@YES`). |
| `artwork`  | `NSData`   | The data of the `UIImage` (use `UIImagePNGRepresentation`). The artwork image should be 60x60 (note that some apps handle this differently with some scale parameter for iPhone + devices). |

If there is no next track available (end of queue for example), simply send a next track message without a metadata dictionary.

## Subscribing to events
NextUp will send notifications (using `CFNotificationCenter`) in two scenarios:
1. When SpringBoard changed the now playing app to the client you support.
2. When the skip button was pressed.

Refer to the code down below. A tip: either find a `sharedInstance` to the queue manager for the `skipNext` and `manualUpdate` methods down below to use or hook the queue manager's init method and subscribe to a custom `NSNotification` event.

One could also register to notifications using `notify_register()` from `<notify.h>`.

```
#define notificationArguments CFNotificationCenterRef center, void *observer, CFStringRef name, const void *object, CFDictionaryRef userInfo
#define subscribe(x, y) CFNotificationCenterAddObserver(CFNotificationCenterGetDarwinNotifyCenter(), NULL, x, CFStringRef(y), NULL, 0);

void manualUpdate(notificationArguments) {
    // Handle manual update event
}

void skipNext(notificationArguments) {
    // Handle skip next event
}

%ctor {
    registerApp();

    subscribe(&manualUpdate, @"se.nosskirneh.nextup/manualUpdate/com.client.app");
    subscribe(&skipNext, @"se.nosskirneh.nextup/skipNext/com.client.app");
}
```
