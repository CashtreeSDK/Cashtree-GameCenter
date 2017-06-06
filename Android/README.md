# Cashtree Game Center Android SDK

- *Last updated : 2017-06-06*
- *Version : 1.1.1*
- Tech Contact : rnd@cashtree.id
- Sales Contact : sales@cashtree.id
- http://www.cashtree.id/

## Inserting SDK

### Importing SDK into Android Projects
cashtreegame_v1.1.1.jar file and add the file to libs directory. When using Android Studio, add jar files to library.

### Adding Dependencies
Add this to your application’s build.gradle:
```java
dependencies {
  compile files('libs/cashtreegame_v1.1.1.jar')
  compile files('libs/okhttp-3.7.0.jar')
  compile files('libs/okio-1.12.0.jar')
}
```

### Adding Permission
In the Package Explorer open the ```AndroidManifest.xml``` of your Android project. Add the ```uses-permission``` tag for ```INTERNET```, ```READ_PHONE_STATE``` and ```GET_ACCOUNTS``` if it's not present already.
```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
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

### Proguard settings
If you are using Proguard, add these lines to your Proguard file:
```txt
-dontwarn okio.**
```

----

## Function Integration
### Init
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;
import com.vitiglobal.cashtree.sdk.Credential;
import com.vitiglobal.cashtree.sdk.Events;
import com.vitiglobal.cashtree.sdk.GameResult;

...
CashtreeGameCenter.Init( ACTIVITY, new Credential("Partner Key", "Partner Secret") );
...
```

If you want to see logs of various SDK actions, you add a ```Debug mode``` parameter.
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;
import com.vitiglobal.cashtree.sdk.Credential;
import com.vitiglobal.cashtree.sdk.Events;
import com.vitiglobal.cashtree.sdk.GameResult;

...
boolean isDebugMode = true;
CashtreeGameCenter.Init( ACTIVITY, new Credential("Partner Key", "Partner Secret", isDebugMode) );
...
```

### Track Event
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;

/* Enum Events
 *     Launch
 *     PlayStart
 *     PlayEnd
 *     PurchaseStart
 *     PurchaseFailed
 *     PurchaseComplete
 */

...
CashtreeGameCenter.TrackEvent( Events type, String... values ); // *values* can pass up to 5 arguments.
...
```

### Track Custom Event
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;

...
CashtreeGameCenter.TrackCustomEvent( String eventName, String... values ); // *values* can pass up to 5 arguments.
...
```

### Game Result
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;

/* Enum GameResult
 *     Win
 *     Lose
 *     Tie
 */

...
CashtreeGameCenter.GameResult( GameResult result, String... values ); // *values* can pass up to 5 arguments.
...
```
