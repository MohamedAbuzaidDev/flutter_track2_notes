# Dialog

## Ex 1

```dart
showDialog(
    context: context,
    builder: (context) => AlertDialog(
        title: const Text("Alert"),
        content: const Text("Do you want to continue?"),
        actions: <Widget>[
            TextButton(
                child: const Text("Cancel"),
                onPressed: () {
                  Navigator.of(context).pop();
                },
            ),
            TextButton(
                child: const Text("OK"),
                onPressed: () {
                  // Handle OK action
                },
            ),
        ],
    )
);
```

## Ex 2

```dart
showDialog(
    context: context,
    builder: (context) => SimpleDialog(
        title: const Text("Alert"),
        children: <Widget>[
            SimpleDialogOption(
                onPressed: () {
                    Navigator.pop(context);
                },
                child: const Text("Option 1"),
            ),
            SimpleDialogOption(
                onPressed: () {
                    Navigator.pop(context);
                },
                child: const Text("Option 2"),
            ),
        ],
    )
);
```

# Snakebar

## Ex

```dart
ScaffoldMessenger.of(context).showSnackBar(
    SnackBar(
        content: const Text("This is a SnackBar"),
        duration: const Duration(seconds: 1),
        action: SnackBarAction(
            label: "Undo",
            onPressed: () {
                // Handle undo action
            },
        ),
    ),
);
```

# Drawer

## Ex

```dart
class MyApp extends StatelessWidget {
  MyApp({super.key});
  GlobalKey<ScaffoldState> ScaffoldKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        key: ScaffoldKey,
        drawer: Drawer(
          child: ListView(
            children: [
              Text('title'),
              ListTile(
                title: Text('home'),
                leading: Icon(Icons.home),
                onTap: (){},
              ),
            ],
          ),
        ),
        appBar: AppBar(),
        body: Container(
          decoration: BoxDecoration(
            border: Border.all(
              color: Colors.blue[400]!,
              width: 2
            ),
            color: Colors.blueGrey[100]
          ),
          alignment: Alignment.center,
          width: 400,
          height: 400,
          padding: const EdgeInsets.all(15),
          margin: const EdgeInsets.all(10),
          child: MaterialButton(onPressed: () {
            ScaffoldKey.currentState!.openDrawer();
          }, child: Text('open menu'),),
        ),
      ),
    );
  }
  
}
```

# PopupButton

## Ex

```dart
class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState(); 
}

class _MyAppState extends State<MyApp> {

  @override
  Widget build (BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          actions: [
            PopupMenuButton(
              icon: Icon(Icons.account_circle),
              onSelected: (value) => print(value),
              onCanceled: () => print('canceled'),
              onOpened: () => print('opened'),
              itemBuilder: (context) => [
              PopupMenuItem(
                child: Text('opt one'),
                value: 'one', 
                onTap: () => print('tab on one'),
              ),
              PopupMenuItem(
                child: Text('opt two'),
                value: 'two', 
              ),
            ])
          ],
        ),
      )
    );
  }
}
```