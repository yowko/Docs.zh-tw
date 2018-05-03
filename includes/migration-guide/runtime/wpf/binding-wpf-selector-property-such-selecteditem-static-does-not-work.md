### <a name="binding-a-wpf-selector-property-such-as-selecteditem-to-a-static-property-does-not-work"></a>將 WPF 選取器屬性 (例如 'SelectedItem') 繫結至靜態屬性無法運作

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，更新繫結屬性時，將資料繫結至靜態屬性的 WPF 選取器屬性 (例如 <xref:System.Windows.Controls.ListBox?displayProperty=name> 或 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 上的 &#39;SelectedItem&#39;) 不會正確地進行更新。|
|建議|此行為在 .NET Framework 4.5 的服務更新中已還原。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|

