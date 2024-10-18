# AnimatedContainer

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> {
  Color boxColor = Colors.red; 
  double boxRadius = 0;
  @override
  Widget build (BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('home page')),
      body: ListView(
        children: [
           const Center(
            child: Text('home page content',
              style:  TextStyle(
                fontSize: 30,
                fontWeight: FontWeight.bold
              ),
            ),
          ), 
          Center(
            child: AnimatedContainer(
              duration: Duration(seconds: 3),
              decoration: BoxDecoration(
                color: boxColor,
                borderRadius: BorderRadius.circular(boxRadius) 
              ),
              width: 100,
              height: 100,
              onEnd: () {
                setState(() {
                  boxColor = Colors.red;
                  boxRadius = 0;
                });
              },
            )
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              boxColor = Colors.green;
              boxRadius = 50;
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```

# AnimatedCrossFade

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> {
  bool toggleBoxes = true; 
  @override
  Widget build (BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('home page')),
      body: ListView(
        children: [
           const Center(
            child: Text('home page content',
              style:  TextStyle(
                fontSize: 30,
                fontWeight: FontWeight.bold
              ),
            ),
          ), 
          Center(
            child: AnimatedCrossFade(
              firstChild: Container(
                child: Text('one'),
                width: 100,
                height: 100,
                color: Colors.red,
              ),
              secondChild: Container(
                child: Text('two'),
                width: 100,
                height: 100,
                color: Colors.green,
              ),
              crossFadeState: toggleBoxes? CrossFadeState.showFirst: CrossFadeState.showSecond,
              duration: Duration(seconds: 3),
              firstCurve: Curves.bounceIn,
              secondCurve: Curves.bounceInOut,
            )
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              toggleBoxes = !toggleBoxes;
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```

# AnimatedDefaultTextStyle

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> {
  double fs = 20; 
  Color fc = Colors.red;
  @override
  Widget build (BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('home page')),
      body: ListView(
        children: [
           const Center(
            child: Text('home page content',
              style:  TextStyle(
                fontSize: 30,
                fontWeight: FontWeight.bold
              ),
            ),
          ), 
          Center(
            child: AnimatedDefaultTextStyle(
              child: Text('animated text'),
              duration: Duration(seconds: 3),
              style: TextStyle(
                fontSize: fs,
                color: fc
              ),
              curve: Curves.fastOutSlowIn,
            )
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              fc = Colors.green;
              fs = 30;
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```

# AnimatedOpacity & Padding

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> {
  double op = 0; 
  double pd = 5;
  @override
  Widget build (BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('home page')),
      body: ListView(
        children: [
           const Center(
            child: Text('home page content',
              style:  TextStyle(
                fontSize: 30,
                fontWeight: FontWeight.bold
              ),
            ),
          ), 
          Center(
            child: AnimatedOpacity(
              opacity: op,
              duration: Duration(seconds: 3),
              child: Container(
                width: 100,
                  height: 100,
                  color: Colors.red,
                child: AnimatedPadding(
                padding: EdgeInsets.all(pd),
                duration: Duration(seconds: 3),
                child: Container(
                  width: 50,
                  height: 50,
                  color: Colors.white,
                ),
              ),
              ),
            )
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              pd = 20;
              op = 1;
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```

# AnimatedPosioned

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> {
  double t = 0; 
  double l = 0;
  @override
  Widget build (BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('home page')),
      body: ListView(
        children: [
           const Center(
            child: Text('home page content',
              style:  TextStyle(
                fontSize: 30,
                fontWeight: FontWeight.bold
              ),
            ),
          ), 
          Center(
            child: Container(
              color: Colors.red,
              width: 400,
              height: 400,
              child: Stack(
                children: [
                  AnimatedPositioned(
                    child: Container(
                      color: Colors.green,
                      width: 100,
                      height: 100,
                    ), 
                    duration: Duration(seconds: 3),
                    top: t,
                    left: l,
                  )
                ],
              ),
            )
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              t = 300;
              l = 300;
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```