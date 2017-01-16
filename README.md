# Cashtree Game Center SDK

- *Last updated : 2016-12-20*
- *Version : 1.0*

## Inserting SDK

### Importing SDK into Android Projects

cashtreegame.jar file and add the file to libs directory. When using Android Studio, add jar files to library.

### Adding Dependencies

No other library is required to use the SDK.

## Function Integration
### Init
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;
import com.vitiglobal.cashtree.sdk.Credential;

...
CashtreeGameCenter.Init( ACTIVITY, new Credential("Partner Key", "Partner Secret") );
...
```

### Track Event
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;

/* Enum CashtreeGameCenter.Events
 *     Launch
 *     PlayStart
 *     PlayEnd
 *     PurchaseStart
 *     PurchaseFailed
 *     PurchaseComplete
 */

...
CashtreeGameCenter.TrackEvent( CashtreeGameCenter.Events type, String... values ); // *values* can pass up to 5 arguments.
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

/* Enum CashtreeGameCenter.GameResult
 *     Win
 *     Lose
 *     Tie
 */

...
CashtreeGameCenter.GameResult( CashtreeGameCenter.GameResult result );
...
```