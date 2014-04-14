spawncamping-tribble
====================

Testing Firebase on Android with PhoneGap.

Requirements:

* Git clone this repo
* Install PhoneGap 
* Connect your Android device and enable USB debugging
* Run ```adb devices```. It should return something like this:
    ```
    0170d697618b27e6    device
    ```


```
cd spawncamping-tribble
```

Run the app:

```
phonegap run android --device
```

Use python SimpleHTTPServer to run the app locally:

```
cd www && python -m SimpleHTTPServer 1234
```
