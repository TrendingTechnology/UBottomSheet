<p><img src="https://github.com/OfTheWolf/UBottomSheet/blob/master/Logo.png" alt="Next Level" style="max-width:100%;"></p>

# UBottomSheet

[![Language](https://img.shields.io/badge/language-swift%205-brightgreen)](https://cocoapods.org/pods/UBottomSheet)
[![Version](https://img.shields.io/cocoapods/v/UBottomSheet.svg?style=flat)](https://cocoapods.org/pods/UBottomSheet)
[![License](https://img.shields.io/cocoapods/l/UBottomSheet.svg?style=flat)](https://cocoapods.org/pods/UBottomSheet)
[![Platform](https://img.shields.io/cocoapods/p/UBottomSheet.svg?style=flat)](https://cocoapods.org/pods/UBottomSheet)

|  | Features |
|:---------:|:---------------------------------------------------------------|
| &#128205; | Apple Maps bottom sheet behaviour |
| &#9875;   | Supports panning with UIScrollView and UIView |
| &#127762; | Allows adding dimmable background view |
| &#128241; | Set sheet content as UIViewController or UINavigationController |
| &#128214; | Navigation inside sheet with UINavigationController |
| &#127752; | Add one to many sheet stop positions|
| &#127919; | Change sheet position programmatically |
| &#127744; | Present as many sheet as you want |
| &#128640; | Move multiple sheets simultaneously or seperately |
| &#127993; | Rubber banding |
| &#128075; | Dismiss at bottom |

## Demo

![Demo](https://github.com/OfTheWolf/UBottomSheet/blob/master/anim.gif)


## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

Bottom sheet child view controllers must conform to the Draggable protocol.

```swift
class MapsDemoBottomSheetController: UIViewController, Draggable{
    @IBOutlet weak var tableView: UITableView!
      
    override func viewDidLoad() {
        super.viewDidLoad()
        
        //adds pan gesture recognizer to draggableView()
        sheetCoordinator?.startTracking(item: self)
        
        tableView.delegate = self
        tableView.dataSource = self
    }

//  MARK: Draggable protocol implementations

    var sheetCoordinator: UBottomSheetCoordinator? 

    func draggableView() -> UIScrollView? {
        return tableView
    }
}

```

Create a UBottomSheetCoordinator from the main view controller. Use the UBottomSheetCoordinator to add and configure the sheet.

```swift

// parentViewController: main view controller that presents the bottom sheet
let sheetCoordinator = UBottomSheetCoordinator(parent: parentViewController)

let vc = UIStoryboard(name: "Main", bundle: nil).instantiateViewController(withIdentifier: "MapsDemoBottomSheetController") as! MapsDemoBottomSheetController

vc.sheetCoordinator = sheetCoordinator

sheetCoordinator.addSheet(vc, to: parentViewController)
```


## Requirements
ios9.0+, Xcode10+

## Installation

UBottomSheet is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'UBottomSheet'
```

## See Also

[TwitterProfile](https://github.com/OfTheWolf/TwitterProfile) Nested scroll view behaviour of Twitter Profile screen.

## Author

uğur, uguboz@gmail.com

## License

UBottomSheet is available under the MIT license. See the LICENSE file for more info.
