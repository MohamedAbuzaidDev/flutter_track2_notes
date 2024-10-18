# What is ListView?

ListView is a scrollable list of widgets arranged linearly. By default, it scrolls vertically, but it can also scroll horizontally. ListView is efficient and flexible, making it ideal for displaying a long list of items.

# Types

## ListView (Default Constructor)

The basic ListView takes an array of widgets and creates a scrollable list. This method is ideal when you have a small and finite number of items.

```dart
ListView(
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

## ListView.builder

The ListView.builder constructor is more efficient for large or dynamically generated lists. It only builds the items that are visible on the screen, making it memory-efficient.

```dart
ListView.builder(
  itemCount: 100,  // Number of items
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
)
```

## ListView.separated

The ListView.separated constructor allows you to insert separators between the items, which can be useful for creating dividers or different section layouts.

```dart
ListView.separated(
  itemCount: 5,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
  separatorBuilder: (context, index) {
    return Divider();
  },
)
```