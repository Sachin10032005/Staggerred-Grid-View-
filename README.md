# Flutter Staggered Grid View Demo

This project demonstrates a simple implementation of a Staggered Grid View in Flutter, using the `flutter_staggered_grid_view` package.

## Getting Started

To run this project, you need to have Flutter installed. For instructions on how to install Flutter, visit the [official documentation](https://flutter.dev/docs/get-started/install).

### Packages Used
- `flutter_staggered_grid_view`: A Flutter package for displaying staggered grids with variable-sized tiles.

### Installation

1. Add the following dependency to your `pubspec.yaml` file:

    ```yaml
    dependencies:
      flutter:
        sdk: flutter
      flutter_staggered_grid_view: ^0.6.1  # Make sure to use the latest version
    ```

2. Run the following command to install the dependencies:

    ```bash
    flutter pub get
    ```

### Code Overview

The following Dart code demonstrates how to create a staggered grid layout using the `StaggeredGrid` widget in Flutter.

```dart
import 'package:flutter/material.dart';
import 'package:flutter_staggered_grid_view/flutter_staggered_grid_view.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Staggered Grid View'),
        ),
        body: Padding(
          padding: const EdgeInsets.all(8.0),
          child: StaggeredGrid.count(
            crossAxisCount: 4,    // Total number of columns in the grid
            mainAxisSpacing: 8,    // Spacing between grid items (vertically)
            crossAxisSpacing: 8,   // Spacing between grid items (horizontally)
            children: List.generate(10, (index) {
              return StaggeredGridTile.count(
                crossAxisCellCount: 2,    // Width of each tile in terms of number of columns
                mainAxisCellCount: index.isEven ? 2 : 3,  // Height varies for even and odd items
                child: Container(
                  color: Colors.blueAccent,
                  child: Center(
                    child: CircleAvatar(
                      backgroundColor: Colors.white,
                      child: Text('$index'),
                    ),
                  ),
                ),
              );
            }),
          ),
        ),
      ),
    );
  }
}
