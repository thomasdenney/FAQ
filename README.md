#iOS Programming FAQ

This FAQ originated because I noticed a lot of questions were getting repeated on [/r/iosprogramming](http://reddit.com/r/iosprogramming) so I've decided to write short and sweet answers to all the common questions here. This is a curated list, and I am actively looking for contributions for both questions and answers, so please submit pull requests.

##Prerequisites

###Do I need a Mac?

Yes.

###But I heard that I can use technology X to do iOS development on Windows/Linux/Google Glass.

Irrespective of what you use to write your app, you will still need Xcode on a Mac to compile your app and submit it to the App Store.

###Where can I get the developer tools?

You can download Xcode from the [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). You can also download the [Xcode 6 beta](https://developer.apple.com/swift/resources/) if you're a registered developer (you don't need to be a paid member).

###Which Mac should I get?

Depends what your budget is. Any Mac that can run the latest version of OSX and has more than 4GB of RAM will do. I would recommend Mac Mini or a MacBook Air.

###Do I need an iOS device?

Yes, it's imperative that you test your app on a real device before you submit it to the App Store. Besides, you'll probably want to get a feel for how other iOS apps work before you write one.

###Which iOS device?

Provided that you can run iOS 8 you will be fine. This includes the iPod Touch 5G, iPhone 4S+ and iPad 2+. Remember, however, that Apple may not support all of these devices for iOS 9. If you're tight on budget then an iPad Mini with Retina Display or an iPod Touch is the best option.

###Do I have to pay $99 for the developer license to get my app on the App Store?

Yes.

###So you're saying that I need to buy a Mac, iOS device and developer license?

Yes.

##Tools

###Is PaintCode any good?

Yes. Opacity and Opacity Express are some cheaper alternatives that also export Objective-C rendering code, and the vector editor in Opacity is a little better for some tasks. However, only use PaintCode if it is going to save you time and resources - if you aren't using much beyond the default iOS icons or you don't have dynamic graphics you probably don't need it.

###Should I use AppCode or Xcode?

For most developers, Xcode is a fantastic IDE and the vast majority of iOS and OSX developers use it as their primary IDE. The benefit of Xcode is that it gets all the new features - such as the SpriteKit scene editor, Swift support, etc - straight away, whereas AppCode and other apps take longer to get new features. That said, AppCode does offer some fantastic and unique features.

##SDK

###Where can I find some great examples of Objective-C code?

* [NSHipster](http://nshipster.com)
* [objc.io](http://objc.io)
* [Big Nerd Ranch](http://www.bignerdranch.com)

###Do I have to use storyboards?

No, you can alternatively use XIB files or generate your user interface in code. However, if you've got a small app storyboards can be very useful for visualising the structure and flow of the app.

###What should I use to store my app's data?

* **Core Data**. A really easy to use managed object graph based on top of SQLite. For most apps this is the best solution because you are able to take advantage of `NSFetchedResultsController` to make your table and collection views really slick and update automatically. Unlike other technologies Core Data has a very strict [concurrency model](https://developer.apple.com/library/ios/documentation/cocoa/Conceptual/CoreData/Articles/cdConcurrency.html), which you need to know about before you get started
* **FMDB/SQLite**. If you aren't going to directly use Core Data then using SQLite is your next best bet. If you're on iOS, the best way to interact with SQLite is through [FMDB](https://github.com/ccgus/fmdb). Instead of letting Core Data manage your model objects you can create your own model objects from the results of SQL queries. This means that you can use your own concurrency model (although FMDatabaseQueue is a super easy solution to thread safety). If you're interested in something somewhere between FMDB and Core Data you might want to try Marco Arment's [FCModel](https://github.com/marcoarment/FCModel), which is based off of Brent Simmons' description of [how he uses FMDB](http://www.objc.io/issue-4/SQLite-instead-of-core-data.html)
* **NSUserDefaults**. Don't store your object graph in NSUserDefaults, as this is a simple key-value store that is great for storing settings. Do not store sensitive data such as credentials, OAuth tokens or in-app purchase receipts on NSUserDefaults - use [Keychain](https://developer.apple.com/library/ios/documentation/Security/Conceptual/keychainServConcepts/02concepts/concepts.html) for this instead

###What frameworks should I use for my game?

* [**Unity**](http://unity3d.com) allows you to write cross platform 2/3D games in C# or JavaScript. It provides the vast majority of the tools that you need to get started, and is appropriate for the most iOS games
* **SpriteKit** is a framework for iOS 7+ and OSX 10.9+ that allows for the development of sprite based 2D games in Xcode. If you aren't bothered about platform lock in and you want to develop a 2D game then this is probably your best bet
* **SceneKit** has been available since OSX 10.8 and iOS 8. It can integrate with SpriteKit and hugely simplifies the amount of work needed to get 3D graphics on the screen (compared to OpenGL or Metal). If your developing a casual 3D game then SceneKit is a great option
* **OpenGL/Metal** are the low-level APIs available on iOS for 3D graphics. Most developers will not need to use Metal as this is primarily targeted at game engine developers (and requires a lot more work to do basic 3D graphics). OpenGL is now reasonably easy to get started with thanks to GLKit (iOS 5+) but you still have to do a lot of C and manual memory management. For most casual games SpriteKit or SceneKit are better solutions, and for more complex games it will be easier to use a ready made engine like Unity. However, OpenGL is a good way of learning how 3D graphics work
* **Cocos2D** is a framework similar to SpriteKit (it allows you to develop 2D games in Objective-C) however has the benefit of being cross platform. Cocos2D is a little older in its API style than SpriteKit, however has a wealth of tutorials and documentation available for it

**I would quite like to have a list here of games that use each framework**

###Where can I get good advice?

* [StackOverflow](http://stackoverflow.com/questions/tagged/ios)
* [Apple Developer Forums](https://devforums.apple.com/index.jspa)
* [NSHipster](http://nshipster.com)
* [objc.io](http://objc.io)
* [Big Nerd Ranch](http://www.bignerdranch.com)
* [/r/iosprogramming](http://reddit.com/r/iosprogramming)

###Do I need to support iOS 6?

No. Currently around 90% of all iOS devices are on iOS 7, and by next spring it will be a similar figure for iOS 8. You'll miss out on using the latest APIs and you'll likely have to write a lot of additional code in order to properly support iOS 6. The only major reason to support versions earlier than iOS 7 is if you are developing for a specific audience (such as schools) that may have older devices (such as the iPad 1).

##Common tasks

###How can I change my apps' font?

###How can I request some JSON from the web?

###I want to build a client app for web service X. How do I get started?

Firstly, you need to confirm that you can legally access the data and that the service provider is OK with you making the app. Secondly, you need to confirm that the service has an API of some sort that you can use. This may be anything from a JSON/XML REST API to a full iOS SDK. If it doesn't, you may be able to scrape HTML but this will be very unreliable as your app would break if the page layout changed.

###My UITextView doesn't scroll properly on iOS 7.

Neither does mine. PSPDFKit has a [fix for it though](http://petersteinberger.com/blog/2014/fixing-uitextview-on-ios-7/).

##Language

In general, the programming language you work in is only half of the challenge of learning to build an app. The other, more important half, is the frameworks. Often it is easiest to learn to build an app in Objective-C because the vast majority of documentation, tutorials and support are currently written for Objective-C. Therefore it is often easier to learn the basics with Objective-C before applying them in the language of your choice.

###Should I learn Objective-C or Swift first?

At the moment, Objective-C. Swift is a fantastic language, however knowing Objective-C will be very valuable for any iOS programmer for at least the next few years. It will likely be a lot quicker to get started with Objective-C than Swift at the moment because most tutorials are written for it.

###Can I write an iOS app in JavaScript?

Yes, technologies like [PhoneGap](http://phonegap.com) and [Appcelerator](http://www.appcelerator.com/titanium/) make this pretty easy.

###Can I write an iOS app in Ruby?

Yes, with [RubyMotion](http://www.rubymotion.com).

###Can I write an iOS app in Java?

Yes, sort of with [XMLVM](http://www.xmlvm.org/iphone/). But please don't.

###Can I write an iOS app in Python?

You can write games in Python using [Kivy](http://kivy.org/#home). You can also write and run Python on your iOS device with [Pythonista](http://omz-software.com/pythonista/).

###Should I write my app with Xamarin?

If you are targeting multiple platforms or the majority of your app's code is 'business logic' then Xamarin may be a really good option, especially if you are already familiar with C#.

###Is there an easy reference for Objective-C block syntax?

[fuckingblocksyntax.com](http://fuckingblocksyntax.com)

###Is there an easy reference for Swift closure syntax?

[fuckingclosuresyntax.com](http://fuckingclosuresyntax.com)

###Why does Foundation classes start with NS?

Objective-C doesn't support namespaces, so all classes are prefixed with the framework or developer abbreviation. NS = NextStep, which is the company that Apple bought in the 90s and was used to develop OSX and iOS. For your own classes Apple recommends that you use your own three letter prefix, especially if you publish the code.

##Cloud and Web

###Should I use iCloud Core Data?

A few years ago the answer was absolutely not. Since iOS 7 Apple has hugely improved the quality of the APIs used for syncing data. If you have a simple data model that isn't going to get shared between users that you want to sync between devices then Core Data is a very good choice. [objc.io has a great guide to get you started](http://www.objc.io/issue-10/icloud-core-data.html).

###Should I use CloudKit?

CloudKit is a bit different to iCloud Core Data. The benefits of CloudKit is that you get access to a NoSQL-style database, binary data storage and the ability to share data between users. Another very cool feature is that it can send notifications *automatically* to users based on the results of data queries that run in the cloud. In order to use CloudKit your user will have to a web connection because nothing is cached locally.

###Should I use Parse?

Parse has proven to be a very popular technology owned by Facebook. Its advantages over CloudKit is that it is multi-platform (Android support too) and supports earlier versions of iOS. However, CloudKit has the advantage that identity is automatic (linked with the users' iCloud account) and it is cheaper.

###Should I run my own servers/VPS?

For most developers the answer is probably not. There are three main reasons to run your own servers:

* You need something more than a 'dumb cloud' (i.e. you need something other than the client to manipulate your data)
* You are likely to grow to an enormous Instagram-like scale
* You are experienced in managing servers and it would be cheaper for you to go with [AWS](https://aws.amazon.com)/[Heroku](http://heroku.com)/[DigitalOcean](http://digitalocean.com)/[Linode](https://www.linode.com) than some other service

**Be warned:** running your own servers is a lot of work, and you probably don't need to if you are working on your first cloud-based app.

##Design

###What apps are good for UI design?

Most vector or image edidotrs are OK. [Photoshop](http://www.photoshop.com), [Pixelmator](http://pixelmator.com), [Sketch](http://bohemiancoding.com/sketch/) and [Opacity](http://likethought.com/opacity/) are all great options on the Mac. You may also like to try Facebook's [Origami](http://facebook.github.io/origami/) for interaction design.

###Any good design guides or blogs?

The [Human Interface Guidelines](https://developer.apple.com/library/prerelease/ios/documentation/UserExperience/Conceptual/MobileHIG/index.html#//apple_ref/doc/uid/TP40006556-CH66-SW1) are a great place to start - but remember that they're guidelines and not rules. Blogs like [made for iOS 7](http://madeforios7.tumblr.com) and [iOS App designs](http://iosappdesigns.tumblr.com) also showcase great app design.

###Any tips for good design?

* Justify every pixel of your UI - is a control essential for most people? 
* Is this interaction obvious? A lot of apps use really interesting combinations of swipes, pinches and taps but make sure that your users will know how to use them
* Use AutoLayout and prepare for size classes. Apple wasn't even remotely subtle at WWDC '14 that AutoLayout is designed to work for multiple screen sizes and classes...

##Community

###What developer blogs can I read?

* [NSHipster](http://nshipster.com)
* [objc.io](http://objc.io)
* [Swift](http://www.apple.com/legal/internet-services/itunes/appstorenotices/)
* [Ash Furrow](http://ashfurrow.com)
* [Brent Simmons](http://inessential.com)
* [NSBlog (Mike Ash)](https://mikeash.com/pyblog/)
* **To be continued...**

###What podcasts can I listen to?

####Programming specific

* [Build and Analyze](http://5by5.tv/buildanalyze) (finished)
* [Build Phase](http://podcasts.thoughtbot.com/buildphase)
* [CocoaConf](http://cocoaconf.com/podcast)
* [Core Intuition](http://www.coreint.org)
* [Debug](http://www.imore.com/debug)
* [Developing Perspective](http://developingperspective.com)
* [Edge Cases](http://edgecasesshow.com)
* [Identical Cousins](http://identicalcousins.net) (finished)
* [iDeveloper](http://ideveloper.tv)
* [iOhYes](http://iohyespodcast.com)
* [iPhreaks](http://iphreaksshow.com)
* [Iterate](http://www.imore.com/iterate)
* [NSBrief](http://nsbrief.com)
* [Ray Wenderlich](http://www.raywenderlich.com/rwpodcast)
* [The Record](http://therecord.co)
* [Release Notes](http://releasenotes.tv)
* [Springboard](http://springboardshow.com) (finished?)

####Apple and technology general

* [Accidental Tech Podcast](http://atp.fm)
* [Hypercritical](http://5by5.tv/hypercritical)
* [iMore](http://www.imore.com/imore-show)
* [The Prompt](http://5by5.tv/prompt)
* [The Talk Show (John Gruber)](http://daringfireball.net/thetalkshow/)
* [Technically Correct](http://www.tcp.fm)

##Third party code

###Where can I find great third party code?

[CocoaPods](http://cocoapods.org). CocoaPods is a tool used by iOS developers that makes it really easy to integrate open source code into your iOS app. Several sites, such as [Cocoa Controls](https://www.cocoacontrols.com/platforms/ios/controls?cocoapods=t) keep track of these. 

###Should I use CocoaPods/third party code?

The answer for most people is yes. The vast majority of CocoaPods are licensed under MIT or Apache, which means that you can include them in your app, even if it is closed source and commercial. There is a good guide to different licenses [here](http://blog.codinghorror.com/pick-a-license-any-license/). Also consider whether you are including third party code because it will save you time or you don't know how to do something. You ideally do not want to be in a position where you are publishing an app with code in that you don't know how it works, because you need to support your app.

###Any great CocoaPods that I should know about?

* [AFNetworking](http://github.com/AFNetworking/AFNetworking)
* **To be continued...**

##The App Store

###Will Apple accept my app?

If you need to ask the question, probably not. To quote the [App Store review guidelines](https://developer.apple.com/appstore/resources/approval/guidelines.html):

> We will reject Apps for any content or behavior that we believe is over the line. What line, you ask? Well, as a Supreme Court Justice once said, "I'll know it when I see it". And we think that you will also know it when you cross it.

###How can I monetize my free app?

Ads or in-app purchase. If you include ads, make sure that you use them conservatively and they don't ruin the user experience. You'll generally need >100,000 users to begin to make a decent amount of money from ads. If you have in-app purchases, then make sure that they offer content or features that genuinely offering something useful.

###Is it OK to include 'rate my app' dialogs?

From Apple's standpoint, yes. But please don't. They're annoying and [many people don't like them](http://daringfireball.net/linked/2013/12/05/eff-your-review) - some people even do 'revenge one star reviews', but this is probably a bit extreme. A better approach is to include a link to your App Store page in your app's settings or about screen. If you are going to include the dialog, make sure you do the following:

* Only show the dialog after the user has used the app for a reasonable amount of time (after all, it isn't worth showing it to users that use your app for a few minutes and then delete it, because they would probably give it a low rating)
* Show the rating at the most once per version
* Always provide an option to never show the dialog again, and if the user picks this option then *don't ever show it again!*

###Which ad service should I use?

When you're looking at picking an ad service you need to take into account the eCPM and the fill rate. The eCPM is how much money you make, on average, from 1000 ad impressions. Fill rate is the percentage of ad requests that were successfully responded to with an ad. Ideally this should be as close to 100% as possible. Generally [AdMob](http://www.google.com/ads/admob/) has a higher rate than [iAd](http://iad.apple.com).

**I'm keen to have some statistics here comparing average fill rate and eCPM for different services, if anyone has it**

###How can I get my app featured by Apple?

Build an awesome app that attracts their attention 😀. You can't pay or bribe Apple to feature your app.

###Where should I advertise my app?

Facebook, Twitter, your website, iAd, the web...

###My app isn't getting many reviews. What can I do?

Respect your current users and do not spam them with requests for reviews, as above. It isn't really their issue that you aren't getting reviews. You could find a way of politely requesting a review, such as the end of an update description.

###What can I do if somebody copies my app?

If there is a copyright issue (i.e. they're purporting to be you, or they've literally cloned your apps' entire UI and feature set) you need to go through the [iTunes Content Dispute](http://www.apple.com/legal/internet-services/itunes/appstorenotices/) system.

##Contracting

###I have an amazing idea for an app. Where can I hire a developer?

###I've written a great app but I don't do design. Where can I hire a designer?