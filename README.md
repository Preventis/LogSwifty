# LogSwifty

Simple logging for Swift.

## Installation

LogSwifty can be installed using [Carthage](https://github.com/Carthage/Carthage). After installing Carthage just add LogSwifty to your Cartfile as follows:

```ruby
github "benjohnde/LogSwifty" ~> 1.0
```

## Usage

```swift
import LogSwifty

class AppDelegate {
  func applicationDidFinishLaunching(_ application: UIApplication) {
    Log.add(logger: Log.debug)
  }
}

class SomeViewController: UIViewController {
  override func viewDidLoad() {
    super.viewDidLoad()
    Log.v("hi there!")
  }
}
```

### For other use cases create your own Logger.

```swift
import LogSwifty

class RESTLogger: Logger {
    func log(message: Message) {
        // post the log somewhere
        SomeHttpService.postLogMessage(message)
    }
}

class AppDelegate {
  func applicationDidFinishLaunching(_ application: UIApplication) {
    Log.add(logger: RESTLogger())
    #if DEBUG
      Log.add(logger: Log.debug)
    #endif
  }
}
```
