# Notes on Objective-C language

1. [Foundation](https://developer.apple.com/documentation/foundation) framework in iOS contains basic classes for data-types, collections amd OS services. Most classes with `NS` prefix {NeXT Step} belong to this Framework
1. Good resource to learn basics [Tutorials Point](https://www.tutorialspoint.com/objective_c/)
1. [Info.plist](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html) is meta data that is used for application on different purposes
1. You can look at StoryBoards's XML [Instructions here](https://stackoverflow.com/questions/30567998/how-to-open-storyboard-as-xml-source)
1. [Fabric.io](http://fabric.io/) is a tool that is used for different purposes:
    1. Crashlytics: For tracking crashes {similar to what Sentry dones}
    1. Digit {This is used for authentication}
    1. Twitter Kit {This is used for twitter interaction}
1. Xcode has conecept of Workspace and Project. More on it [from Stackoverflow](https://stackoverflow.com/questions/21631313/xcode-project-vs-xcode-workspace-differences)
1. [Cocoapods] is used for Package Management and Dependencies. Following are some of the Pods we've used:
    1. [SDWebImage](https://github.com/rs/SDWebImage)
    1. [Fabric](https://cocoapods.org/pods/Fabric)
    1. [CZPicker](https://github.com/chenzeyu/CZPicker)
1. There are two methods of saving global data {between View Controllers}. They are [more on this](http://chrisrisner.com/31-Days-of-iOS-Day-10-Singletons-and-the-AppDelegate):
    1. AppDelegate
        - didFinishLaunching is used for
            - Notification Handling
            - Sharing Resources
            - Handling Backward Compatability
    1. Singleton
1. In Objective-C: File beginning with `.m` files are implmentations {this is where **Definitions** are}. `.h` files are header files {this is where **Declarations** are}
1. [Core Data](https://en.wikipedia.org/wiki/Core_Data) is a persistance storeage used for storing data onto mobiles
1. [ARC: Automatic Reference Counting](https://clang.llvm.org/docs/AutomaticReferenceCounting.html) is a garbage collection technique used for memory management in iOS Applications
1. [NSURL](https://developer.apple.com/documentation/foundation/nsurl) is a class used for making HTTP {GET/POST} requests calls.
1. [NSJSONSerialization](https://developer.apple.com/documentation/foundation/nsjsonserialization) is used for JSON de/serialization
1. [NSUserDefaults](https://code.tutsplus.com/tutorials/ios-sdk-working-with-nsuserdefaults--mobile-6039) class is another method of persisting data {e.g. Session related information}
1. [UICollectionView](https://developer.apple.com/documentation/uikit/uicollectionview) is used for showing information in grids.
1. [UITableView](https://developer.apple.com/documentation/uikit/uitableview) is used for showing row like information

## Resources

1. [Tutorials Point](https://www.tutorialspoint.com/objective_c/)
1. [31 Days of iOS](http://chrisrisner.com/31-Days-of-iOS)
