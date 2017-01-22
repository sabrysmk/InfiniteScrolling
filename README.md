# InfiniteScrolling

[![CI Status](http://img.shields.io/travis/Vishal Singh Panwar/InfiniteScrolling.svg?style=flat)](https://travis-ci.org/Vishal Singh Panwar/InfiniteScrolling)
[![Version](https://img.shields.io/cocoapods/v/InfiniteScrolling.svg?style=flat)](http://cocoapods.org/pods/InfiniteScrolling)
[![License](https://img.shields.io/cocoapods/l/InfiniteScrolling.svg?style=flat)](http://cocoapods.org/pods/InfiniteScrolling)
[![Platform](https://img.shields.io/cocoapods/p/InfiniteScrolling.svg?style=flat)](http://cocoapods.org/pods/InfiniteScrolling)


## Add infinite scrolling to collection view.

This is a basic implementation to add infinite scrolling behaviour in a `UICollectionView`.

## Usage
Usage is pretty simple. `InfiniteScrollingBehaviour` has one designated initiliser.

```swift
init(withCollectionView collectionView: UICollectionView, andData dataSet: [InfiniteScollingData], delegate: InfiniteScrollingBehaviourDelegate, configuration: CollectionViewConfiguration = .default)
```

`InfiniteScrollingData` is a protocol which your modal needs to conform to. Right now its an empty protocol, but for scalability purpose, I felt like adding data set as collection of custom protocol instead of `Any`.

`CollectionViewConfiguration` can be used to tweak some behaviour of the infinite scrolling.
You neeed to provide `maxNumberOfCellsOnScreen` and `scrollingDirection`. Based on these two properties, boundary elements are added as well as size for cell is calculated.
By default, `InfiniteScrollingBehaviour` has a `CollectionViewConfiguration` with `maxNumberOfCellsOnScreen` as 5 and `scrollingDirection` as `horizontal`.

Currently it only supports 1 element in a line with 0 inter item spacing and line spacing.

Incase you need to have infinite scrolling with pagination, enable pagination in the collectionView and pass in `maxNumberOfCellsOnScreen` 1.

## InfiniteScrollingBehaviourDelegate
The delegate has two methods.

```swift
func configuredCell(forItemAtIndexPath indexPath: IndexPath, originalIndex: Int, andData data: InfiniteScollingData, forInfiniteScrollingBehaviour behaviour: InfiniteScrollingBehaviour) -> UICollectionViewCell
func didSelectItem(atIndexPath indexPath: IndexPath, originalIndex: Int, andData data: InfiniteScollingData, inInfiniteScrollingBehaviour behaviour: InfiniteScrollingBehaviour) -> Void
```
First is a required method. Implementation needs to provide a configured `UICollectionViewCell` based on following parameters.
- **indexPath:** Actual indexpath in the collectionView.
- **originalIndex:** Index in the original data set.
- **data**: `InfiniteScollingData` which will be used to configure your cell.


**Note:**If the number of elements in the data set is smaller than the `maxNumberOfCellsOnScreen`, than it automatically adjusts boundary to repeat the same elements on screen.


## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

<div style='position:relative;padding-bottom:178%'><iframe src='https://gfycat.com/ifr/PointedPaltryHusky' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

## Requirements

- Minimum iOS version: 9.0
- Swift: 3.0
- Xcode 8

## Installation

InfiniteScrolling is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "InfiniteScrolling"
```


## License

InfiniteScrolling is available under the MIT license. See the [LICENSE](LICENSE) file for more info.
