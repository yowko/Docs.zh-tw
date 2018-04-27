### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>WPF TreeViewItem 必須在 TreeView 內使用

|   |   |
|---|---|
|詳細資料|4.5 中引進一項變更，限制在 <xref:System.Windows.Controls.TreeView?displayProperty=name> 外使用 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 項目。 在下列狀況下可能會發生這種情形：<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 的視覺化父代不是面板。 (針對 <xref:System.Windows.Controls.TreeView?displayProperty=name> 產生的 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 會有一個面板作為其父代)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 是 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> 的子系，可作為清單控制項 (ListBox、DataGrid、ListView 等) 的「項目主控件」。 不需要啟用虛擬化。</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> 是項目捲動 (<code>ScrollUnit=&quot;Item&quot;</code>)。</li><li>使用者可呼叫 <code>VirtualizingStackPanel.MakeVisible(v)</code> 將項目 <code>v</code> 捲動至檢視中。 這可以透過數種方式明確或隱含完成；最常見的方式可能是直接按一下 <code>v</code> 以提供鍵盤焦點。</li><li>從 <code>v</code> 到 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> 的視覺化父代鏈結會通過 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>。</li></ul>換句話說，在 <xref:System.Windows.Controls.TreeView?displayProperty=name> 外使用 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>，然後使用者點選 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 的子系將其帶入檢視時，就會看到此問題。 如果 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 沒有可設定焦點的子系，則絕不會看到此問題。 例如，當 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 是 DataTemplate 的根項目時，就會遇到此問題。 遇到此問題時，WPF 架構內會出現 InvalidCastException。|
|建議|未來將針對此問題提供 Hotfix。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|

