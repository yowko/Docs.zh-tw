### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impl 必須將收到的相同參數傳遞給 WriteEvent (再加上識別碼)

|   |   |
|---|---|
|詳細資料|執行階段現在會強制執行指定下列作業的合約：定義 ETW 事件方法之衍生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 的類別在呼叫基底類別 <code>EventSource.WriteEvent</code> 方法時，必須在事件識別碼後面接著傳遞 ETW 事件方法的相同目的地引數。|
|建議|如果 <xref:System.IndexOutOfRangeException?displayProperty=name> 讀取來自於違反此合約之事件來源的處理中 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> 資料，則會擲回 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 例外狀況。|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|

