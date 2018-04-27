### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 會卸除焦點

|   |   |
|---|---|
|詳細資料|從其中一個 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 的 <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> 事件處理常式呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit> 會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 失去焦點。|
|建議|此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。 或者，您也可以在呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name> 之後明確重新選取 <xref:System.Windows.Controls.DataGrid?displayProperty=name>，來避免此 Bug。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

