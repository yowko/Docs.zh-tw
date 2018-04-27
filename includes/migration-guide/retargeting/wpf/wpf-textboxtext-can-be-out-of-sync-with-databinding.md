### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text 可能與資料繫結不同步

|   |   |
|---|---|
|詳細資料|在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text> 屬性會反映資料繫結屬性值先前的值。|
|建議|這應該不會產生負面影響。 不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 屬性設為 <code>false</code> 還原舊有行為。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

