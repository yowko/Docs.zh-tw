### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>ICommand.CanExecuteChanged 事件行為在 .NET 4.5 中已變更

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，除非事件的傳送者是引發事件的相同物件，否則會忽略 <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name>。 此 Bug 已在 .NET Framework 4.5 服務更新中進行修正。|
|建議|此錯誤 (bug) 在 .NET Framework 4.5 服務版本中已修正，因此可藉由確保 .NET Framework 處於最新狀態，或升級至 .NET Framework 4.5.1 來避免。 或者，您也可以修改使用 <xref:System.Windows.Input.ICommand?displayProperty=name> 的應用程式程式碼，以確保引發 <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> 命令的傳送者與引發事件的物件相同。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|分析器|<ul><li>CD0084</li></ul>|

