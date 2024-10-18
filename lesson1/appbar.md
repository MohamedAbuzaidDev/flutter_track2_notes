# What is the AppBar Widget?

The `AppBar` widget is a material design widget in Flutter that displays a toolbar at the top of the Scaffold widget.

It provides consistent structure, navigation options, and action buttons across screens.

# AppBar Example

```dart
AppBar(
    //! Basic Structure
    title: const Text('Flutter App'),
    leading: const Icon(Icons.menu),
    actions: [
      IconButton(icon: const Icon(Icons.search), onPressed: () {}),
      IconButton(icon: const Icon(Icons.more_vert), onPressed: () {}),
    ],
    //! Customizing AppBar
    backgroundColor: Colors.blue,
    elevation: 10,
    shadowColor: Colors.red,
    centerTitle: true,
    toolbarHeight: 100,
    //! Flexable Space
    flexibleSpace: Container(
      alignment: Alignment.center,
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          colors: [Colors.blue, Colors.purple],
        ),
      ),
      height: double.infinity,
      child: const Text(
        'New App',
        style: TextStyle(fontSize: 25, color: Colors.white),
      ),
    ),
  )
```

# Sliver AppBar

For more complex app bars that allow scrollable backgrounds, Flutter offers `SliverAppBar`, which can be used with scrolling views to provide flexible space and collapsing effects.

```dart
// Inside Scaffold Body
CustomScrollView(
  slivers: [
    SliverAppBar(
      title: Text('SliverAppBar'),
      expandedHeight: 200.0,
      flexibleSpace: FlexibleSpaceBar(
        background: Image.network(
          'https://codetheweb.blog/assets/img/posts/css-advanced-background-images/cover.jpg',
          fit: BoxFit.cover,
        ),
      ),
    ),
    SliverList(
      delegate: SliverChildBuilderDelegate(
        (BuildContext context, int index) {
          return ListTile(
            title: Text('Item #$index'),
          );
        },
      ),
    ),
  ],
)
```