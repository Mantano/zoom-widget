# Flutter zoom widget

<img src="https://raw.githubusercontent.com/semakers/zoom-widget/master/header.png" data-canonical-src="https://raw.githubusercontent.com/semakers/zoom-widget/master/header.png" width="300" height="200" />

With this widget you can create a customizable canvas in which you can **zoom** in flutter.

It is possible to customize virtually all the canvases of the canvas such as color, background color, acitvate and deactivate scrolls, change the color of scrolls, modify the sensitivity of the zoom, the initial zoom enters other aspects found in the construction of the Zoom class.

## Installation

Add to pubspec.yaml:

```yaml
dependencies:
mno_zoom_widget: ^0.1.0
```



## How to use

You only need to create an instance of the Zoom class in the child of your Scaffold or within the widget of your choice, within the child attribute, put the widget that you want to zoom in and the width and height of the canvas where it will be made zoom.

### Reader-like capability

The ```axis``` property has been added to allow to embed the Zoom widget into a PageView. This widget supports to move in the same axis as the PageView to avoid the scrolling while the Zoom widget has not reached the edge. If the Zoom widget is not embedded in a PageView, this property can be ignored.

### Import

```dart
import 'package:mno_zoom_widget/zoom_widget.dart';
```

### Simple example


```dart
Zoom(
    maxZoomWidth: 1800,
    maxZoomHeight: 1800,
    child: Center(
        child: Text("Happy zoom!!"),
    )
);
```

### Callbacks

It is possible to obtain the **x and y position** of our canvas with respect to the scrolls and and the **zoom and scale** of our canvas using two simple callbacks in our Zoom instance.

```dart
Zoom(
    maxZoomWidth: 1800,
    maxZoomHeight: 1800,
    onTap: (){
        print("Widget clicked");
    }
    onPositionUpdate: (Offset position){

        print(position);

    },
    onScaleUpdate: (double scale,double zoom){

        print("$scale  $zoom");

    },
    child: Center(
        child: Text("Happy zoom!!"),
    )
);
```
<img src="https://raw.githubusercontent.com/semakers/zoom-widget/master/first_example.gif" data-canonical-src="https://raw.githubusercontent.com/semakers/zoom-widget/master/first_example.gif" width="250" height="500" />

### Customize properties


Customizing the properties you can get amazing results.

- width (Depreceted) **double**. 
- height (Depreceted) **double**. 
- maxZoomWidth **double**. 
- maxZoomHeight **double**. 
- backgroundColor **Color**.
- canvasColor **Color**.
- onPositionUpdate() **Callaback**.
- onScaleUpdate() **Callaback**.
- onTap() **Callaback**.
-  scrollWeight **double**.
- opacityScrollBars **double 0.0-1.0**.
- colorScrollBars **Color**.
- centerOnScale **bool**.
- initZoom **double 0.0-1.0**.
- enableScroll **bool**.
- zoomSensibility  **double**.
- doubleTapZoom **bool**.
- axis **Axis**.

### Customized properties example


```dart
Zoom(
    maxZoomWidth: 1800,
    maxZoomHeight: 1800,
    canvasColor: Colors.grey,
    backgroundColor: Colors.orange,
    colorScrollBars: Colors.purple,
    opacityScrollBars: 0.9,
    scrollWeight: 10.0,
    centerOnScale: true,
    enableScroll: true,
    doubleTapZoom: true,
    zoomSensibility: 2.3,
    initZoom: 0.0,
    axis: Axis.horizontal,
    onTap: (){ 
        print("Widget clicked");
    }
    onPositionUpdate: (position){
        setState(() {
            x=position.dx;
            y=position.dy;
        });
    },
    onScaleUpdate: (scale,zoom){
        setState(() {
            _zoom=zoom;
        });
    },
    child: Center(
        child: Text("x:${x.toStringAsFixed(2)} y:${y.toStringAsFixed(2)} zoom:${_zoom.toStringAsFixed(2)}",style: TextStyle(color: Colors.deepPurple,fontSize: 50),),
    ),
);
```

<img src="https://raw.githubusercontent.com/semakers/zoom-widget/master/second_example.gif" data-canonical-src="https://raw.githubusercontent.com/semakers/zoom-widget/master/second_example.gif" width="250" height="500" />

## Examples

### Mobile

In the **example/mobile** folder you will find the example ready to run with ***Flutter*** using the commands.

```shell
flutter pub get
```

```shell
flutter run
```

### Desktop

In the **example/desktop** folder you will find the example ready to run with ***Hover***.

[Hover - Run Flutter apps on the desktop with hot-reload](https://github.com/go-flutter-desktop/hover)



