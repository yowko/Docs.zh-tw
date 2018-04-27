### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>在具有不同像素高度之項目的簡單列表中進行項目捲動

|   |   |
|---|---|
|詳細資料|<xref:System.Windows.Controls.ItemsControl?displayProperty=name> 使用虛擬化 (<code>IsVirtualizing=true</code>) 及項目捲動 (<code>ScrollUnit=Item</code>) 顯示集合時，以及捲動控制項以顯示高度 (以像素為單位) 與其相鄰項目不同的項目時，<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> 會逐一查看集合中的所有項目。 此 UI 在逐一查看期間沒有回應；如果集合很大，這可視為停止回應。此逐一查看行為會出現在其他情況下，即使在 .Net 之前的版本中也一樣。 例如，在下列情況會發生這種情況：如果在發現像素高度不同的項目時進行像素捲動 (<code>ScrollUnit=Pixel</code>)，以及如果在發現子系項目數與其相鄰項目不同的項目時進行階層式資料項目捲動 (例如，在已啟用群組的 <xref:System.Windows.Controls.TreeView?displayProperty=name> 或 <xref:System.Windows.Controls.ItemsControl?displayProperty=name> 中)。針對項目捲動和不同像素高度的情況，.Net 4.6.1 中引進了逐一查看，以修正階層式資料配置中的 Bug)。  如果是單層式資料 (沒有階層)，則不需要逐一查看，而且 .Net 4.6.2 在此情況下不會這麼做。|
|建議|如果在 .Net 4.6.1 中出現逐一查看行為，但舊版中並未出現 (亦即，如果 <xref:System.Windows.Controls.ItemsControl?displayProperty=name> 是在具有不同像素高度之項目的簡單列表中進行項目捲動)，則有兩種解決方式：<ol><li>安裝 .Net 4.6.2。</li><li>安裝 .Net 4.6.1 的 Hotfix HR 1605。</li></ol>|
|範圍|次要|
|版本|4.6.1|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

