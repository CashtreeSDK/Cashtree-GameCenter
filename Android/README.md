# Cashtree Game Center Android SDK

- *Last updated : 2017-03-02*
- *Version : 1.0.1*
- Tech Contact : rnd@cashtree.id
- Sales Contact : sales@cashtree.id
- http://www.cashtree.id/

## Inserting SDK

### Importing SDK into Android Projects
cashtreegame_v1.0.1.jar file and add the file to libs directory. When using Android Studio, add jar files to library.

### Adding Dependencies
No other library is required to use the SDK.

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
