1. create a stateful widget and use with state class the folowing classes:
   1. SingleTickerProviderStateMixin > when using single animation controller
   2. TickerProviderStateMixin > when using multible animation controllers
2. initialize two Objects
   1. AnimationController? _controller;
   2. Animation? _animation;
3. add initState to do:
   1. set _controller value = AnimationController(vsync: this, duration: Duration(seconds: 3));
   2. set _animation = Tween(begin: 50.0, end: 200.0).animate(_controller!)..addStatusListener((status) {
      if(status == AnimationStatus.completed) {
        print('animation finished');
      }
      print(status);
    })..addListener(() {
      print(_animation!.value);
    });
    3. note that: addStatusListener > run function when status changed like begin and end
    4. note that: addListener > run function when animation value changed like 50, 70, ..., 200

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> with SingleTickerProviderStateMixin {
  AnimationController? _controller;
  Animation? _animation;

  void initState() {
    _controller = AnimationController(vsync: this, duration: Duration(seconds: 3));
    _animation = Tween(begin: 50.0, end: 200.0).animate(_controller!)..addStatusListener((status) {
      if(status == AnimationStatus.completed) {
        print('animation finished');
      }
      print(status);
    })..addListener(() {
      print(_animation!.value);
    });
    _controller!..forward();
    super.initState();
  }

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
            
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: () {
            setState(() {
              
            });
          }, child: Text('show changes'),)
        ],
      )
    );
  }
}
```

4. add setState inside addListener and you can run by button or initState on Container

```dart
import "package:flutter/material.dart";

void main() => runApp(const HomePageApp());

class HomePageApp extends StatefulWidget {
  const HomePageApp({super.key});
  @override
  State<HomePageApp> createState() => _HomePageAppState();
}

class _HomePageAppState extends State<HomePageApp> with SingleTickerProviderStateMixin {
  AnimationController? _controller;
  Animation? _animation;

  void initState() {
    _controller = AnimationController(vsync: this, duration: Duration(seconds: 3));
    _animation = Tween(begin: 50.0, end: 200.0).animate(_controller!)..addStatusListener((status) {
      if(status == AnimationStatus.completed) {
        print('animation finished');
      }
      print(status);
    })..addListener(() {
      setState(() {});
      print(_animation!.value);
    });
    // _controller!..forward();
    super.initState();
  }

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
            child: Transform.rotate(
              angle: -3.14 / 2 * _animation!.value,
              child: Container(
                color: Colors.red,
                width: 100,
                height: 100,
              ),
            ),
          ),
          Container(height: 100,),
          OutlinedButton(onPressed: (){
            _controller!..forward();
          }, child: Text('run animation'))
        ],
      )
    );
  }
}
```


# Ex 2

```dart
import 'package:flutter/material.dart';

class ExplicitAnimationDemo extends StatefulWidget {
  @override
  _ExplicitAnimationDemoState createState() => _ExplicitAnimationDemoState();
}

class _ExplicitAnimationDemoState extends State<ExplicitAnimationDemo> with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _animation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(seconds: 2),
      vsync: this,
    );

    _animation = Tween<double>(begin: 0, end: 300).animate(_controller)
      ..addListener(() {
        setState(() {});
      });

    // Start the animation
    _controller.forward();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Explicit Animation Example')),
      body: Center(
        child: Container(
          width: _animation.value,
          height: _animation.value,
          color: Colors.blue,
          child: FlutterLogo(size: 75),
        ),
      ),
    );
  }
}
```

## Combining Animations Using AnimatedBuilder

```dart
import 'package:flutter/material.dart';

class AnimationBuilderDemo extends StatefulWidget {
  @override
  _AnimationBuilderDemoState createState() => _AnimationBuilderDemoState();
}

class _AnimationBuilderDemoState extends State<AnimationBuilderDemo> with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _animation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(seconds: 3),
      vsync: this,
    )..repeat(reverse: true);

    _animation = Tween<double>(begin: 50, end: 200).animate(_controller);
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('AnimatedBuilder Example')),
      body: Center(
        child: AnimatedBuilder(
          animation: _animation,
          builder: (context, child) {
            return Container(
              width: _animation.value,
              height: _animation.value,
              color: Colors.green,
              child: child,
            );
          },
          child: FlutterLogo(size: 50),
        ),
      ),
    );
  }
}
```

## Curves in Animation

```dart
_animation = Tween<double>(begin: 0, end: 300).animate(
  CurvedAnimation(parent: _controller, curve: Curves.bounceOut)
);
```