### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>在某些情況下，工作流程現在會擲回原始例外狀況，而不是 NullReferenceException

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 和舊版中，工作流程活動的 Execute 方法擲回 <xref:System.Exception.Message> 屬性為 <code>null</code> 值的例外狀況時，System.Activities 工作流程執行階段會擲回 <xref:System.NullReferenceException?displayProperty=name>，進而遮罩原始的例外狀況。在 .NET Framework 4.7 中，會擲回之前遮罩的例外狀況。|
|建議|如果您的程式碼依賴處理 <xref:System.NullReferenceException?displayProperty=name>，請將它變更為攔截可能會從自訂活動擲回的例外狀況。|
|範圍|次要|
|版本|4.7|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

