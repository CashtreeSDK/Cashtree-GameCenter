# Cashtree Game Center SDK

- *Last updated : 2016-12-20*
- *Version : 1.0*

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
CashtreeGameCenter.TrackEvent( CashtreeGameCenter.Events type, String... values ); // values는 최대 5개까지 전달할 수 있습니다
...
```

### Track Custom Event
```java
import com.vitiglobal.cashtree.sdk.CashtreeGameCenter;

...
CashtreeGameCenter.TrackCustomEvent( String eventName, String... values ); // values는 최대 5개까지 전달할 수 있습니다
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