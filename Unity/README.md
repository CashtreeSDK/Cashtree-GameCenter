# Cashtree Game Center Unity SDK

- *Last updated : 2017-03-02*
- *Version : 1.0.1*
- Tech Contact : rnd@cashtree.id
- Sales Contact : sales@cashtree.id
- http://www.cashtree.id/

###CashtreeGameCenter Package Contains:
* Plugins/
  * `Cashtree.cs`
  * Android/
    * `CashtreeAndroid.cs`
    * `cashtreegame_v1.x.x.jar`
    * `CashtreeAndroidManifest.xml`
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

Replace {PARTNER_TEST1}, {PARTNER_SECRET1} with your actual "Partner Key" and "Partner Secret". If you don't know about these things, please send to email this address rnd@cashtree.id .

----

## Function Integration
### Init
```cs
using com.vitiglobal.cashtree.sdk;

...
Cashtree.Init ("PARTNER_TEST1", "PARTNER_SECRET1");
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
