### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>使用自訂 DataTemplates 時，會斷斷續續無法捲動至 ItemsControls (例如 ListBox 和 DataGrid) 中的底部項目

|   |   |
|---|---|
|詳細資料|在某些情況下，.NET Framework 4.5 中的 Bug 會導致在使用自訂 DataTemplates 時，ItemsControls (例如 <xref:System.Windows.Controls.ListBox?displayProperty=name>、<xref:System.Windows.Controls.ComboBox?displayProperty=name>、<xref:System.Windows.Controls.DataGrid?displayProperty=name> 等) 無法捲動至其底部項目。 如果嘗試捲動第二次 (在向上捲動之後)，則會再次運作。|
|建議|此問題在 .NET Framework 4.5.2 中已修正，因此可藉由升級至該版 .NET Framework (或更新版本) 來解決。 此外，使用者仍可將捲軸拖曳至這些集合中的最後一個項目，但可能需要嘗試兩次才能成功。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|

