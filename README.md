# TrackWeight

**Turn your MacBook's trackpad into a precise digital weighing scale**

[TrackWeight](
https://github.com/adithyardy/TrackWeight.git) is a macOS application that transforms your MacBook's trackpad into an accurate weighing scale by leveraging the Force Touch pressure sensors built into modern MacBook trackpads.

To use it yourself:

1. Open the scale
2. Rest your finger on the trackpad
3. While maintaining finger contact, put your object on the trackpad
4. Try to put as little pressure on the trackpad while still maintaining contact. This is the weight of your object

## How It Works

TrackWeight utilizes the [Open Multi-Touch Support library](https://github.com/Kyome22/OpenMultitouchSupport) to gain private access to all mouse and trackpad events on macOS. This library provides detailed touch data including pressure readings that are normally inaccessible to standard applications.

The key insight is that trackpad pressure events are only generated when there's capacitance detected on the trackpad surface - meaning your finger (or another conductive object) must be in contact with the trackpad. When this condition is met, the trackpad's Force Touch sensors provide precise pressure readings that can be calibrated and converted into weight measurements.

### Calibration Process

The weight calculations have been validated by:
1. Placing the MacBook trackpad directly on top of a conventional digital scale
2. Applying various known weights while maintaining finger contact with the trackpad
3. Comparing and calibrating the pressure readings against the reference scale measurements
4. Ensuring consistent accuracy across different weight ranges

It turns out that the data we get from MultitouchSupport is already in grams!

## Requirements

- **macOS 13.0+** (for Open Multi-Touch Support library compatibility)
- **MacBook with Force Touch trackpad** (2015 or newer MacBook Pro, 2016 or newer MacBook)
- **App Sandbox disabled** (required for low-level trackpad access)
- **Xcode 16.0+** and **Swift 6.0+** (for development)

## Installation

1. Clone this repository
2. Open in Xcode
3. Disable App Sandbox in the project settings (required for trackpad access)
4. Build and run the application

## Limitations

- **Finger contact required**: The trackpad only provides pressure readings when it detects capacitance (finger touch), so you cannot weigh objects directly without maintaining contact
- **Surface contact**: Objects being weighed must be placed in a way that doesn't interfere with the required finger contact
- **Metal objects**: Metal objects may be detected as a finger touch, so you may need to place a piece of paper or a cloth between the object and the trackpad to get an accurate reading

## Technical Details

The application is built using:
- **SwiftUI** for the user interface
- **Combine** for reactive data flow
- **Open Multi-Touch Support library** for low-level trackpad access
