# What is the BottomSheet in Flutter?

- The BottomSheet is used to display content from the bottom of the screen.

- It is commonly used for actions, settings, options, or additional content without requiring full navigation.

# Types

- **Modal BottomSheet:** A temporary bottom sheet that can be dismissed by swiping down or tapping outside.
  
- **Persistent BottomSheet:** A bottom sheet that remains visible and can interact with the rest of the UI.

## Modal BottomSheet

- A modal BottomSheet is a temporary, dismissible bottom sheet that overlays the entire screen.
  
- It’s ideal for quick actions or menus that can be dismissed by swiping down or tapping outside.

### Example

- using by `showModalBottomSheet`
- 
```dart
void _showModalBottomSheet(BuildContext context) {
  showModalBottomSheet(
    context: context,
    builder: (BuildContext context) {
      return Container(
        height: 200,
        color: Colors.white,
        child: Center(
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: <Widget>[
              Text('This is a Modal BottomSheet'),
              ElevatedButton(
                child: Text('Close BottomSheet'),
                onPressed: () {
                  Navigator.pop(context);
                },
              ),
            ],
          ),
        ),
      );
    },
  );
}
```

## Persistent BottomSheet

- A persistent BottomSheet is a type of bottom sheet that stays on the screen and can interact with other parts of the UI.
  
- It’s commonly used for tasks where continuous interaction with the bottom sheet is needed.

### Example

- using by `Scaffold.bottomSheet` or `showBottomSheet`
  
```dart
void _showPersistentBottomSheet(BuildContext context) {
  Scaffold.of(context).showBottomSheet(
    (context) => Container(
      height: 200,
      color: Colors.lightBlueAccent,
      child: Center(
        child: Text('This is a Persistent BottomSheet'),
      ),
    ),
  );
}
```
