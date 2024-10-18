## Ex 

```dart
class MyApp extends StatelessWidget {
  MyApp({super.key});

  int indx = 0;
  List<Widget> listWidgits = [
    Text('page home'),
    Text('page setting'),
  ];
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
          bottomNavigationBar: BottomNavigationBar(
            currentIndex: indx,
            onTap: (val) {
              // use setState
            },
            backgroundColor: Colors.blue,
            selectedItemColor: Colors.red,
            unselectedItemColor: Colors.white,
            items: [
              BottomNavigationBarItem(icon: Icon(Icons.home), label: 'home'),
              BottomNavigationBarItem(icon: Icon(Icons.settings), label: 'setting'),
            ],
          ),
          body: Container(
            child: listWidgits.elementAt(indx), // need statefull
          ),
        ),
    );
  }
  
}
```