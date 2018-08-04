# Contents
- [Purpose](#purpose)
- [Snapkit](#snapkit)
- [iOS Centric](#ioscentric)
- [Contributing](#contributing)

## Purpose
Snapchat’s Snapkit is new and there are holes in the documentation. As developers implement Snapkit, they will develop best practices. This document exists to help developers obtain success with Snapkit and document the best practices they come across.

There will be copy/paste form the [Snapkit documentation](https://docs.snapchat.com/docs/). The purpose of which is to make it easy to see what is there as well as what should be there

## Snapkit
### LoginKit
#### Getting Started

In your app project in Xcode, add SCSDKCoreKit.framework and SCSDKLoginKit.framework into General > Embedded Binaries.

>Add the following fields in your application’s Info.plist file:
>- SCSDKClientId (string): Your application’s client ID

It isn’t clear what client ID means. The documentation immediately before this says

>Requirements
>Client ID from the developer portal
>iOS version 10.0+

However, there is absolutely nothing in the developer portal with a label **client ID**. Do they mean **OAUTH CLIENT ID**? (I suspect so, but have an email out to them asking about this)
And here's the ever helpful Developer Portal itself which makes things clear as mud

<img src='https://raw.githubusercontent.com/bbookman/Snapchat-Snapkit-DIY-Docs/images/devportal1.png'>


### iOS Centric
I’m working to integrate Snapkit into an existing iOS Swift project, and so I’ll be adding mostly iOS centric information. As this repository is open, anyone is welcome to add Android info.

### Contributing
Please fork and submit pull requests

### Bugs and feature requests
File bugs or requests as any other repository. Feel free to work on anything that is there.

### Contact
For most things, file bugs. anything else:
[@saganone1](http://twitter.com/saganone1) on twitter
