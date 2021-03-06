NVActivityIndicatorView
===================

[![Build Status](https://travis-ci.org/ninjaprox/NVActivityIndicatorView.svg?branch=master)](https://travis-ci.org/ninjaprox/NVActivityIndicatorView)
[![Cocoapods Compatible](https://img.shields.io/cocoapods/v/NVActivityIndicatorView.svg)](https://img.shields.io/cocoapods/v/NVActivityIndicatorView.svg)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

# Introduction
NVActivityIndicatorView is a collection of nice loading animations.

This is original a fork from [DGActivityIndicatorView](https://github.com/gontovnik/DGActivityIndicatorView), inspired by [Loaders.css](https://github.com/ConnorAtherton/loaders.css), written in Swift with full implementation of animations.

You can also find Objective-C version of this [here](https://github.com/ninjaprox/DGActivityIndicatorView).

# Demo
![alt tag](https://raw.githubusercontent.com/ninjaprox/NVActivityIndicatorView/master/Demo.gif)

For first-hand experience, just open the project and run it.

# Animation types

1. BallPulse
2. BallGridPulse
3. BallClipRotate
4. SquareSpin
5. BallClipRotatePulse
6. BallClipRotateMultiple
7. BallPulseRise
8. BallRotate
9. CubeTransition
10. BallZigZag
11. BallZigZagDeflect
12. BallTrianglePath
13. BallScale
14. LineScale
15. LineScaleParty
16. BallScaleMultiple
17. BallPulseSync
18. BallBeat
19. LineScalePulseOut
20. LineScalePulseOutRapid
21. BallScaleRipple
22. BallScaleRippleMultiple
23. BallSpinFadeLoader
24. LineSpinFadeLoader
25. TriangleSkewSpin
26. Pacman
27. BallGridBeat
28. SemiCircleSpin
29. BallRotateChase
30. Orbit
31. AudioEqualizer

# Installation

## Cocoapods

Install Cocoapods if need be

```bash
$ gem install cocoapods
```

Add NVActivityIndicatorView in your `Podfile`

```bash
use_frameworks!

pod 'NVActivityIndicatorView'
```

Then, run the following command

```bash
$ pod install
```
## Carthage

Install Carthage if need be

```bash
$ brew update
$ brew install carthage
```

Add NVActivityIndicatorView in your `Cartfile`

```bash
github "ninjaprox/NVActivityIndicatorView"
```

Run `carthage` to build the framework and drag the built `NVActivityIndicatorView.framework` into your Xcode project.

## Manual

Copy NVActivityIndicatorView folder to your project. That's it.

# Usage

Firstly, import NVActivityIndicatorView

```swift
import NVActivityIndicatorView
```

## Initialization

Then, there are multiple ways you can create NVActivityIndicatorView:

- Use it in storyboard by changing class of any `UIView` to `NVActivityIndicatorView`
This will use default values white, .BallSpinFadeLoader, 0 for color, type and padding respectively.

- Create with specified type, color and padding

```swift
NVActivityIndicatorView(frame: frame, type: type, color: color, padding: padding)
```

Any of the last three arguments can be omitted. If an argument is omitted it will use the default values which are white, .BallSpinFadeLoader, 0 for color, type and padding respectively.
Therefore, you can also create NVActivityIndicatorView using any of the following:

- Specify only frame, type and color
```swift
NVActivityIndicatorView(frame: frame, type: type, color: color)
```

- Specify only frame, type and padding
```swift
NVActivityIndicatorView(frame: frame, type: type, padding: padding)
```

- Specify only frame, color and padding
```swift
NVActivityIndicatorView(frame: frame, color: color, padding: padding)
```

- Specify only frame and type
```swift
NVActivityIndicatorView(frame: frame, type: type)
```

- Specify only frame and color
```swift
NVActivityIndicatorView(frame: frame, color: color)
```

- Specify only frame and padding
```swift
NVActivityIndicatorView(frame: frame, padding: padding)
```

- Specify only frame
```swift
NVActivityIndicatorView(frame: frame)
```

## Start/Stop animation

Start animation

```swift
activityIndicatorView.startAnimation()
```

Stop animation

```swift
activityIndicatorView.stopAnimation()
```

## UI blocker

You can use `NVActivityIndicatorView` as UI blocker for `UIViewController` by conforming `NVActivityIndicatorViewable` protocol.

```swift
class ViewController: UIViewController, NVActivityIndicatorViewable { }
```

Start animation

```swift
startActivityAnimating(size, message) // plus other parameters as when initializing
```

Stop animation

```swift
stopActivityAnimating()
```

## Change properties

If you use `NVActivityIndicatorView` in storyboard, you can change these properties in Attributes inspector tab of Utilities panel.

Use one of values (case-insensitive) in [Animation types](#animation-types) for `Type Name`.

Specify individual properties after initialization:

- Specify type
```swift
activityIndicatorView.type = .LineScale
```

- Specify color
```swift
activityIndicatorView.color = UIColor.redColor()
```

Specify whether activity indicator view should hide once stopped

```swift
activityIndicatorView.hidesWhenStopped = true
```

Get current status of animation
```swift
animation = activityIndicatorView.animating
```

## Change defaults

Change global defaults if needed

###### `NVActivityIndicatorView.DEFAULT_TYPE = .Pacman`

Default type of activity indicator.

###### `NVActivityIndicatorView.DEFAULT_COLOR = UIColor.yellowColor()`

Default color of activity indicator.

###### `NVActivityIndicatorView.DEFAULT_PADDING = CGFloat(5.0)`

Default padding of activity indicator.

###### `NVActivityIndicatorView.DEFAULT_BLOCKER_SIZE = CGSizeMake(60, 60)`

Default size of activity indicator used in UI Blocker.

###### `NVActivityIndicatorView.DEFAULT_BLOCKER_MINIMUM_VISIBLE_TIME = NSTimeInterval(0)`

Default minimum visible time of an activity indicator view in UI Blocker. Its main purpose is to avoid flashes showing and hiding it so fast. For instance, setting it to 200 ms will force every activity indicator to be shown for at least this time (regardless if you call `stopActivityAnimating` before).

###### `NVActivityIndicatorView.DEFAULT_BLOCKER_DISPLAY_TIME_THRESHOLD = NSTimeInterval(0)`

Default minimum time that has to be elapsed (between calls of `startActivityAnimating` and `stopActivityAnimating`) in order to actually display the activity indicator view in UI Blocker. It should be set thinking about what the minimum duration of an activity is to be worth showing it to the user. If the activity ends before this time threshold, then it will not be displayed at all.


# Acknowledgment

Thanks [Connor Atherton](https://github.com/ConnorAtherton) for great loaders and [Danil Gontovnik](https://github.com/gontovnik) for kick-start.

# License

The MIT License (MIT)

Copyright (c) 2016 Nguyen Vinh [@ninjaprox](http://twitter.com/ninjaprox)
