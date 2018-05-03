### <a name="multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>單一 TableLayoutPanel 儲存格中的多個項目可能會重新排列

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，如果將多個項目放在相同的 <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> 儲存格中，可能會以其在 .NET Framework 4.0 中不同的順序顯示。|
|建議|此行為在 .NET Framework 4.5 的服務更新中已還原。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。 此外，請避免多個項目在相同 <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> 儲存格中的模稜兩可情況。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Forms.TableLayoutControlCollection.Add(System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32)?displayProperty=nameWithType></li></ul>|
|分析器|<ul><li>CD0098</li></ul>|

