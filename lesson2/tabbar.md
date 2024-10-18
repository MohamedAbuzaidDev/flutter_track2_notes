# Ex

```dart
class MyApp extends StatelessWidget {
  MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      // Controller for tabBar that exist inside Scaffold > Appbar > bottom || Scaffold > appBar == TabBar
      home: DefaultTabController(
        initialIndex: 1,
        length: 2,
        child: Scaffold(
          appBar: AppBar(title: Text('flutter'), bottom: TabBar(
            indicatorColor: Colors.blue,
            indicatorWeight: 10,
            labelColor: Colors.black,
            unselectedLabelColor: Colors.red,
            tabs: [
            Tab(child: Text('laptop'),),
            Tab(child: Text('pc'),),
          ]),
          ),
          body: Container(
            child: TabBarView(
              children: [
                Text('laptop section'),
                Text('pc section'),
              ],
            ),
          ),
        ),
      ) 
    );
  }
  
}
```