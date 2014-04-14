spawncamping-tribble
====================

Testing Firebase on Android with PhoneGap.

Requirements:

* Git clone this repo
* Install PhoneGap 
* Connect your Android device
* Enable [USB debugging](https://developers.google.com/chrome-developer-tools/docs/remote-debugging)
* Run ```adb devices```. It should return something like this:
    ```
    0170d697618b27e6    device
    ```

    If you don't get a list of connected android devices something went wrong.


```
cd spawncamping-tribble
```

Run the app:

```
phonegap run android --device
```

Use python SimpleHTTPServer to run the app locally on http://0.0.0.0:1234:

```
cd www && python -m SimpleHTTPServer 1234
```

Now that you have the app running both on the Android device and locally click on Chat link. Type a message, hit send, and the message should appear on both devices.

Open a new tab in Chrome navigate to [chrome://inspect/#devices](chrome://inspect/#devices) and you should see an entry:

```
WebView in com.example.FirebasePhoneGapTest (Version/4.0 Chrome/30.0.0.0)
My AngularJS App
file:///android_asset/www/index.html#/chat
```

Click on **Inspect**. 

There's a global ``START`` method keeps sending messages to the chat. It accepts one argument, the time interval between messages in minutes. So

```
START(1)
```

will send a message per minute to the chat. Calling the START method multiple times stops the previous interval and creates a new one. You can also call the global ```msg`` function to send a chat message "manually". These functions are defined in ``www/js/controllers.js``.

**THE ISSUE**

If you define an internal greater than a minute the android app drops the Firebase connection and the logs don't say anything about that. The locally running app keeps the connection indefinitely.
