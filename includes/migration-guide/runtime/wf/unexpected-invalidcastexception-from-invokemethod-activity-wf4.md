### <a name="unexpected-invalidcastexception-from-invokemethod-activity-in-wf4"></a>WF4 中來自 InvokeMethod 活動的非預期 InvalidCastException

|   |   |
|---|---|
|詳細資料|使用利用可為 Null 的參數將方法設為目標的 <xref:System.Activities.Statements.InvokeMethod>，可能會擲回 <xref:System.InvalidCastException?displayProperty=name>。|
|建議|此行為已在 .NET Framework 4.5 服務更新中進行還原。 請更新 .NET Framework 4.5 (或升級至 .NET Framework 4.5.1 或更新版本)，以修正此問題。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Activities.Statements.InvokeMethod.Parameters?displayProperty=nameWithType></li></ul>|
|分析器|<ul><li>CD0088</li></ul>|

