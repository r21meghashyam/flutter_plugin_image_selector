# image_selector

A flutter plugin to select image from gallery and allows user to crop or resize it before submitting.

# Imports

```
    //just for the return type, can use var instead
    import 'dart:typed_data';
```

# Usage

```
    Uint8List pngBytes = await ImageSelector.fromGallery(context);
```

`context` is the BuildContext variable from your current builder.

# Example

```
    void main() async {
        return runApp(CupertinoApp(home: Main()));
    }

    class Main extends StatefulWidget {
        @override
        MainState createState() => MainState();
    }

    class MainState extends State<Main> {
        Image image;
        @override
        Widget build(BuildContext context) {
            return CupertinoPageScaffold(
                child: Center(
                    child: Column(children: [
                        CupertinoButton.filled(
                            child: Text("Select Image"),
                            onPressed: () async{
                                Uint8List pngBytes = await ImageSelector.fromGallery(context);
                                setState(() {
                                    image = Image.memory(
                                        pngBytes,
                                        width: 100,
                                        height: 100,
                                    );
                                });
                            }
                        ),
                        Container(
                            child: image!=null?image:Text("No image selected");
                        )
                    ]
                )
            );
        }
    }
```
