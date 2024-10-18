```dart
import 'package:flutter/material.dart';
class ResponsiveUtil {
  final BuildContext context;

  ResponsiveUtil(this.context);

  // Get screen width
  double screenWidth() {
    return MediaQuery.of(context).size.width;
  }

  // Get screen height
  double screenHeight() {
    return MediaQuery.of(context).size.height;
  }

  Orientation screenOrientation() {
    return MediaQuery.of(context).orientation;
  }

  // Get block size (percent of screen width)
  double horizontalPercentSize(double percentage) {
    return screenWidth() * percentage / 100;
  }

  // Get block size (percent of screen height)
  double verticalPercentSize(double percentage) {
    return screenHeight() * percentage / 100;
  }

  // For responsive text scaling
  double textScaleFactor(double scaleFactor) {
    return MediaQuery.of(context).textScaleFactor * scaleFactor;
  }

  // For responsive padding/margin based on percentage
  EdgeInsets responsivePadding(double horizontalPercent, double verticalPercent) {
    return EdgeInsets.symmetric(
      horizontal: horizontalPercentSize(horizontalPercent),
      vertical: verticalPercentSize(verticalPercent),
    );
  }

  // For responsive padding (all sides)
  EdgeInsets responsiveAllPadding(double percent) {
    return EdgeInsets.all(horizontalPercentSize(percent));
  }

  double defaultSize() {
    return screenOrientation() == Orientation.landscape ?
    screenHeight() * .024 :
    screenWidth() * .024;
  }
}
```


```dart
class ResponsiveLayout extends StatelessWidget {
  final Widget mobileLayout;
  final Widget tabletLayout;
  final Widget desktopLayout;

  const ResponsiveLayout({
    required this.mobileLayout,
    required this.tabletLayout,
    required this.desktopLayout,
  });

  @override
  Widget build(BuildContext context) {
    final screenWidth = MediaQuery.of(context).size.width;

    if (screenWidth > 1000) {
      return desktopLayout;
    } else if (screenWidth > 600) {
      return tabletLayout;
    } else {
      return mobileLayout;
    }
  }
}
```