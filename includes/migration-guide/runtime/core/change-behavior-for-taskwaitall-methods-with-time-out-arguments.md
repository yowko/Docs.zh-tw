### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>含逾時引數之 Task.WaitAll 方法的行為變更

|   |   |
|---|---|
|詳細資料|在 .NET 4.5 中，Task.WaitAll 行為變得更一致。在 .NET Framework 4 中，這些方法的行為不一致。 逾時過期時，如果在方法呼叫之前已完成或取消一個或多個工作，則方法會擲回 <xref:System.AggregateException?displayProperty=name> 例外狀況。 當逾時過期時，如果在方法呼叫之前沒有任何已完成或取消的工作，但是有一個或多個工作在方法呼叫之後進入這兩種狀態，則方法會傳回 false。<br/><br/>在 .NET Framework 4.5 中，如果逾時間隔到期時仍有任何工作正在執行，這些方法多載現在會傳回 false，而只有在取消輸入工作 (不論是在方法呼叫之前或之後)，且沒有其他工作仍在執行時，才會擲回 <xref:System.AggregateException?displayProperty=name> 例外狀況。|
|建議|如果透過攔截 <xref:System.AggregateException?displayProperty=name>來偵測某個工作在叫用 WaitAll 呼叫之前是否已取消，該程式碼應改為透過 IsCanceled 屬性 (例如：.Any(t =&gt; t.IsCanceled)) 執行相同的偵測，因為 .NET 4.6 只會在所有等候的工作在逾時前都已完成時，才會擲回此例外狀況。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|

