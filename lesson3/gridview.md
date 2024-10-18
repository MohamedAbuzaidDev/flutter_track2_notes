# What is GridView?

GridView is a scrollable, 2D array of widgets that can display items in a grid format. It automatically handles both vertical and horizontal scrolling, allowing you to build flexible grid layouts.

# Types of GridView

Flutter provides four types of GridView constructors, each designed for different scenarios:

## GridView.count

This constructor allows you to create a grid with a fixed number of items per row (cross-axis count). It’s the most straightforward and commonly used approach when you know the number of columns.

```dart
GridView.count(
  crossAxisCount: 2,  // Number of columns
  children: <Widget>[
    Container(color: Colors.red, height: 100),
    Container(color: Colors.blue, height: 100),
    Container(color: Colors.green, height: 100),
    Container(color: Colors.yellow, height: 100),
  ],
)
```

## GridView.extent

With this constructor, you define the maximum extent (width) of each item, and Flutter will compute how many items can fit in one row.

```dart
GridView.extent(
  maxCrossAxisExtent: 150,  // Max width of each item
  children: <Widget>[
    Container(color: Colors.red),
    Container(color: Colors.blue),
    Container(color: Colors.green),
    Container(color: Colors.yellow),
  ],
)
```

## GridView.builder

This constructor is ideal for larger grids, especially when the grid is dynamically created. It lazily builds the grid as the user scrolls, making it more efficient for performance.

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,  // Fixed number of columns
  ),
  itemCount: 100,  // Number of items
  itemBuilder: (context, index) {
    return Container(
      margin: EdgeInsets.all(4.0),
      color: Colors.blueAccent,
      child: Center(child: Text('Item $index')),
    );
  },
)
```

# Key Properties of GridView

```dart
GridView.count(
  crossAxisCount: 2,
  crossAxisSpacing: 10.0,
  mainAxisSpacing: 10.0,
  children: <Widget>[
    Container(color: Colors.red),
    Container(color: Colors.blue),
    Container(color: Colors.green),
    Container(color: Colors.yellow),
  ],
)
```