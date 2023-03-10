# Flutter-Notifications
##### This repository is about implementing notifications in flutter app using Firebase backend service.

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

After doing all the steps of integrating firebase into your project 

##### Important packages to install:
 - firebase_messaging
 - firebase_core


## Let's breakdown into code now:

1. Add the following code into main method and make it asynchronous
```
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
```
2. Add this method at the global level to start firebase background serivces
```
Future<void> backgroundHandler(RemoteMessage message) async {}
```
3. Add onBackgroundMessage callback method given by firebase in main method and pass above method in it
```
  FirebaseMessaging.onBackgroundMessage(backgroundHandler);
```
4. Two important firebase methods to call whenever the app starts and best place to use them is in the initState callback of your main screen
```
    //called when app is in terminated state
    FirebaseMessaging.instance.getInitialMessage().then();
    
    //called when app is in foreground state
    FirebaseMessaging.onMessage.listen();

```



## Developers
MIT License

Copyright (c) 2019 TecOrb Technologies

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
