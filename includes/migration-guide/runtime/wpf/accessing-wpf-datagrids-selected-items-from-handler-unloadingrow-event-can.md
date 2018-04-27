### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>從 DataGrid 的 UnloadingRow 事件處理常式存取 WPF DataGrid 的選取項目可能會導致 NullReferenceException

|   |   |
|---|---|
|詳細資料|由於 .NET Framework 4.5 中的 Bug)，涉及移除資料列之 <xref:System.Windows.Controls.DataGrid> 事件的事件處理常式，可能會在它們存取 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 屬性時導致擲回 <xref:System.NullReferenceException?displayProperty=name>。|
|建議|此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

