### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView 擲回 ArgumentOutOfRangeException

|   |   |
|---|---|
|詳細資料|啟用資料行虛擬化，但尚未決定資料行寬度時，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 將以非同步方式運作。  如果資料行在非同步工作進行之前遭到移除，會發生 <xref:System.ArgumentOutOfRangeException?displayProperty=name>。|
|建議|下列任一步驟：<ol><li>升級至 .NET 4.7。</li><li>為 .NET 4.6.2 安裝最新的服務修補程式。</li><li>在 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的非同步回應完成之前，避免移除資料行。</li></ol>|
|範圍|Edge|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

