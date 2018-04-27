### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>修改清單項目時，List&lt;T&gt;.ForEach 可能會擲回例外狀況

|   |   |
|---|---|
|詳細資料|從 .NET 4.5 開始，如果呼叫集合中有任何項目遭到修改，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列舉程式將會擲回 <xref:System.InvalidOperationException?displayProperty=name> 例外狀況。 之前，這不會擲回例外狀況，但可能會造成競爭情形。|
|建議|在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。 不過，若要還原成舊版行為，應用程式可以將目標設為 .NET 4.0。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

