## Flutter Widgets

#### Raw Material Button

```dart
RawMaterialButton(
  fillColor: Colors.white,
  splashColor: Colors.black, 
  shape: StadiumBorder(), // This will create capsule like look
);
```

#### Center

```dart
Center(
	child: Text('Test');
);
```

#### Decorated Box

```dart
DecoratedBox(
	decoration: BoxDecoration(color: Colors.red),
  child: Text('Test'),
);
```

#### Padding

```dart
Padding(padding: const EdgeInsets.all(8), child: Text('test'));
```

iOS has two kinds of scaffold and one for Tabs

```dart
return CupertinoTabScaffold(
	tabBar: CupertinoTabBar(
  	items: [
      BottomNavigationBarItem(icon: CupertinoIcons.book, title: Text('Books')),
      BottomNavigationBarItem(icon: CupertinoIcons.eye, title: Text('Views')),
    ]
  ),
  tabBuilder: (context, i) {
    return TabBarView(builder: (context) {
      return CupertinoPageScaffold(
      	navigationBar: CupertinoNavigationBar(middle: i == 0 ? 'Books' : 'Views'),
        child: Center('This is #$i tab', style:
                      CupertinoTheme.of(context).navLargeTitleTextStyle,
        ),
      )
    },
    )
  }
);
```



### <u>Material Widgets</u>



### <u>Cupertino Widgets</u>

