# Implementations

## Flutter

Cryptofonts is available as a [Flutter package](https://pub.dev/packages/cryptofont).

`SDK | Flutter` `PLATFORMS | Android, OSX, Linux, MacOS, Web, Windows`

### Installing

```
flutter pub add cryptofont
```

This will add a line like this to your package's pubspec.yaml (and run an implicit `flutter pub get`)

```json
dependencies:
  cryptofont: ^1.0.2+1
```

Alternatively, your editor might support `flutter pub get`

Check the docs for your editor to learn more.

### Import it

Now in your Dart code, you can use:

```dart
import 'package:cryptofont/cryptofont.dart';
```

### Usage

```dart
import 'package:cryptofont/cryptofont.dart';

class MyWidget extends StatelessWidget {
  const MyWidget({super.key});

  @override
  Widget build(BuildContext context) {
    // Get the icon code if you need it
    final code = cryptoFontIconMapping[symbol.toLowerCase()];

    return Row(
      children: [
        // Use directly
        const Icon(CryptoFontIcons.btc),
        // Or by using the symbol
        Icon(CryptoFontIcons.fromSymbol("BTC")),
        // Case insensitive, this works too
        Icon(CryptoFontIcons.fromSymbol("btc")),
      ],
    );
  }
} 
```

### Example

**`example/lib/main.dart`**

```dart
import 'package:cryptofont/cryptofont.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(const CryptoFontGalleryApp());
}

class CryptoFontGalleryApp extends StatelessWidget {
  const CryptoFontGalleryApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'CryptoFont Flutter Gallery',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        primarySwatch: Colors.blueGrey,
      ),
      home: const CryptoFontGalleryHome(),
    );
  }
}

class CryptoFontGalleryHome extends StatefulWidget {
  const CryptoFontGalleryHome({
    super.key,
  });

  @override
  State<CryptoFontGalleryHome> createState() => _CryptoFontGalleryHomeState();
}

class _CryptoFontGalleryHomeState extends State<CryptoFontGalleryHome> {
  final TextEditingController _searchController = TextEditingController();
  String searchedTerm = "";

  @override
  void initState() {
    _searchController.addListener(() {
      setState(() {
        searchedTerm = _searchController.text;
      });
    });
    super.initState();
  }

  @override
  void dispose() {
    _searchController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("CryptoFont Flutter Gallery"),
      ),
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(20),
          child: Column(
            children: [
              TextField(
                controller: _searchController,
                decoration: const InputDecoration(
                    hintText: "Search by ticker...",
                    hintStyle: TextStyle(
                      color: Colors.black,
                      fontSize: 18,
                    ),
                    suffixIcon: Icon(Icons.search)),
              ),
              const SizedBox(height: 20),
              Expanded(
                child: LayoutBuilder(
                  builder: (context, constraints) {
                    return GridView.count(
                      crossAxisCount: constraints.maxWidth ~/ 100,
                      children: cryptoFontIconMapping.entries
                          .where((element) => element.key
                              .toUpperCase()
                              .startsWith(searchedTerm.toUpperCase()))
                          .map((e) {
                        final symbol = e.key;
                        return Column(
                          children: [
                            Icon(CryptoFontIcons.fromSymbol(symbol), size: 36),
                            const SizedBox(height: 10),
                            Text(symbol,
                                style: const TextStyle(
                                    fontWeight: FontWeight.w500)),
                          ],
                        );
                      }).toList(),
                    );
                  },
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```
