# What is the Wrap Widget?

The Wrap widget is a layout widget in Flutter that arranges its children in a flow, either horizontally or vertically, and automatically wraps them to the next line or column when space is insufficient.

# Main Properties of Wrap

```dart
Wrap(
  direction: Axis.horizontal,
  verticalDirection: VerticalDirection.up,
  textDirection: TextDirection.rtl,
  alignment: WrapAlignment.center,
  runAlignment: WrapAlignment.center, 
  spacing: 10.0, // the spacing between each child widget in the main axis (horizontal or vertical). It defines how much space to leave between each item.

  runSpacing: 20.0, // This property defines the vertical spacing between rows (if direction is horizontal) or horizontal spacing between columns (if direction is vertical).
  children: <Widget>[
          Container(
            color: Colors.blue,
            width: 200,
            height: 200,
            child:const Center(child: Text("W1", style: TextStyle(
              fontSize: 30
            )))
          ),
          Container(
            color: Colors.red,
            width: 200,
            height: 200,
            child:const Center(child: Text("W2", style: TextStyle(
              fontSize: 30
            )))
          ),
          Container(
            color: Colors.teal,
            width: 200,
            height: 200,
            child:const Center(child: Text("W3", style: TextStyle(
              fontSize: 30
            )))
          ),
          Container(
            color: Colors.indigo,
            width: 200,
            height: 200,
            child:const Center(child: Text("W4", style: TextStyle(
              fontSize: 30
            )))
          ),
          Container(
            color: Colors.orange,
            width: 200,
            height: 200,
            child:const Center(child: Text("W5", style: TextStyle(
              fontSize: 30
            )))
          ),
        ],
)
```