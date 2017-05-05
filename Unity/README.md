# Cashtree Game Center Unity SDK

- *Last updated : 2017-05-05*
- *Version : 1.1.0*
- Tech Contact : rnd@cashtree.id
- Sales Contact : sales@cashtree.id
- http://www.cashtree.id/

### CashtreeGameCenter Package Contains:
* Plugins/
  * `Cashtree.cs`
  * Android/
    * `CashtreeAndroid.cs`
    * `cashtreegame_v1.1.0.jar`
    * `okhttp-3.7.0.jar`
    * `okio-1.12.0.jar`
    * `CashtreeSampleAndroidManifest.xml`
  * Unity/
    * `CashtreeGameEvents.cs`
    * `CashtreeGameResult.cs`
    * `ICashtree.cs`
* Prefabs/
  * `Cashtree.prefab`

## Inserting SDK

### Get the SDK
Download the latest version. Extract the archive in a folder of your choice.

### Add the SDK to your project
Open your project in the Unity Editor and navigate to `Assets → Import Package → Custom Package` Package and select the downloaded Unity package file.

### Integrate the SDK into your app
Add the prefab located at `Assets/Prefabs/Cashtree.prefab` to the first scene.

Edit the parameters of the Cashtree script in the `Inspector menu` of the added prefab.

Replace {Your Partner Key}, {Your Partner Secret} with your actual "Partner Key" and "Partner Secret". If you don't know about these things, please send to email this address rnd@cashtree.id .

### Adding Permission
In the Package Explorer open the ```AndroidManifest.xml``` of your Android project. Add the ```uses-permission``` tag for ```INTERNET``` if it's not present already.
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

### Adding Broadcast receiver
If you are **not using your own broadcast receiver** to receive ```INSTALL_REFERRER``` intent, add the following ```receiver``` tag inside the ```application``` tag in your ```AndroidManifest.xml```.
```xml
<receiver
    android:name="com.vitiglobal.cashtree.sdk.CGCReferrerCatcher"
    android:exported="true" >
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
</receiver>
```

If you are **already using your own broadcast receiver** to receive ```INSTALL_REFERRER``` intent, **add other Install Receivers as ```meta-data```**.
```xml
<receiver
    android:name="com.vitiglobal.cashtree.sdk.CGCReferrerCatcher"
    android:exported="true" >
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    <meta-data android:name="OtherReceiver1" android:value="com.otherapp.sample.SampleReferrerReceiver"/>
</receiver>
```

----

## Function Integration
### Init
```cs
using com.vitiglobal.cashtree.sdk;

...
Cashtree.Init ("{Your Partnet Key}", "{Your Partnet Secret}");
...
```

If you want to see logs of various SDK actions, you add a ```Debug mode``` parameter.
```cs
using com.vitiglobal.cashtree.sdk;

...
bool isDebugMode = true;
Cashtree.Init ("{Your Partnet Key}", "{Your Partnet Secret}", isDebugMode);
...
```

### Track Event
```cs
using com.vitiglobal.cashtree.sdk;

/* Enum Events
 *     Launch
 *     PlayStart
 *     PlayEnd
 *     PurchaseStart
 *     PurchaseFailed
 *     PurchaseComplete
 */

...
Cashtree.TrackEvent (CashtreeGameEvents.PlayStart);
Cashtree.TrackEvent (CashtreeGameEvents.PlayEnd, "a", "b", "c"); // *values* can pass up to 5 arguments.
...
```

### Track Custom Event
```cs
using com.vitiglobal.cashtree.sdk;

...
Cashtree.TrackEventCustom ("StartCustomEvent");
Cashtree.TrackEventCustom ("StartCustomEvent", "a", "b", "c"); // *values* can pass up to 5 arguments.
...
```

### Game Result
```cs
using com.vitiglobal.cashtree.sdk;

/* Enum GameResult
 *     Win
 *     Lose
 *     Tie
 */

...
Cashtree.GameResult (CashtreeGameResult.Win);
Cashtree.GameResult (CashtreeGameResult.Lose, "a", "b", "c"); // *values* can pass up to 5 arguments.
...
```
