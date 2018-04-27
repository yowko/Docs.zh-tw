### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a>lBlockingCollection&lt;T&gt;.TryTakeFromAny 不會再擲回例外狀況

|   |   |
|---|---|
|詳細資料|如果其中一個輸入集合標記為已完成，則 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不會再傳回 -1，而且 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不會再擲回例外狀況。 這項變更能夠讓您在其中一個集合為空集合或已完成，而另一個集合仍有可擷取的項目時處理集合。|
|建議|如果在防止集合完成時，使用了傳回 -1 的 TryTakeFromAny 或擲回的 TakeFromAny 來控制流程，現在應該將這類程式碼變更為使用 <code>.Any(b =&gt; b.IsCompleted)</code> 來偵測該情況。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|

