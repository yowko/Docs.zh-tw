### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek 可透過其 out 參數傳回錯誤的 Null

|   |   |
|---|---|
|詳細資料|在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。|
|建議|此問題在 .NET Framework 4.5.1 中已修正。 升級至該 Framework 將會解決問題。|
|範圍|主要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

