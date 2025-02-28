# ThemeManager

ThemeManager is a most lightweight, powerful, convenient and easiest way to manage your app themes, and also support change text(e.g. language) or other configurations dynamically too.

## Installing ThemeManager

ThemeManager supports CocoaPods and Carthage. ThemeManager is written in Swift.

### Github Repo

You can pull the [ThemeManager Github Repo](https://github.com/azone/ThemeManager) and include the ThemeManager.xcodeproj to build a dynamic or static library.

### CocoaPods

[CocoaPods](https://cocoapods.org/) is a dependency manager for Cocoa projects. For usage and installation instructions, visit their website. To integrate ThemeManager into your Xcode project using CocoaPods, specify it in your `Podfile`:

```ruby
pod 'WYZThemeManager'
```

### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks. To integrate ThemeManager into your Xcode project using Carthage, specify it in your `Cartfile`:

```
github "azone/ThemeManager" "master"
```

### Swift Package Manager

The [Swift Package Manager](https://swift.org/package-manager/) is a tool for automating the distribution of Swift code and is integrated into the swift compiler. It is in early development, but ThemeManager does support its use on supported platforms.

Once you have your Swift package set up, adding ThemeManager as a dependency is as easy as adding it to the dependencies value of your `Package.swift`.

```swift
dependencies: [
    .package(url: "https://github.com/azone/ThemeManager.git", from: "0.2.1")
]
```

![Demo](https://github.com/azone/ThemeManager/raw/master/demo.gif)

## Usage

### 1. implement your self theme, language or other configuration (may be class, struct or anything you want) which must be conform `Theme` protocol.

Example:

 ```swift
import ThemeManager

struct MyTheme: Theme {
    var backgroundColor = UIColor.gray
    var mainColor = UIColor.orange

    var titleFont = UIFont.preferredFont(forTextStyle: .headline)
    var subtitleFont = UIFont.preferredFont(forTextStyle: .subheadline)
    var textColor = UIColor.red

    var buttonTitleColor = UIColor.orange
    var buttonTitleHighlightcolor = UIColor.red
    
    var title = "Default Theme"
}
 ```

### 2. Declare `ThemeManager` instance variable with your default theme in the global scope.

Example:

```swift
let themeManager = ThemeManager(MyTheme())
```

### 3. Put any theme, language or configuration related setups in `setUp` method

Example

```swift
themeManager.setup(view) { (view, theme) in
    view.backgroundColor = theme.backgroundColor
}

themeManager.setup(navigationItem) { (item, theme) in
    item.title = theme.title
}

themeManager.setup(navigationController?.navigationBar) { (bar, theme) in
    bar.tintColor = theme.mainColor
    bar.barTintColor = theme.backgroundColor
}
```

### 4. Change another theme, language or configuration with your theme instance:

```swift
themeManager.apply(otherTheme)
```

## License

ThemeManager is released under the MIT license. [See LICENSE](https://github.com/azone/ThemeManager/blob/master/LICENSE) for details.

