### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Selector 的 SelectionChanged 事件和 SelectedValue 屬性

|   |   |
|---|---|
|詳細資料|從 .Net Framework 4.7.1 開始，<xref:System.Windows.Controls.Primitives.Selector> 在其選取項目變更時，一律會先更新其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性的值，再引發 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件。 這會讓 SelectedValue 屬性與其他選取項目屬性 (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> 和 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>) 一致，在引發事件之前會更新這些選取項目屬性。在 .NET Framework 4.7 和舊版中，在大部分情況下，更新 SelectedValue 會發生在事件之前，但如果選取項目變更是由於變更 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性所造成，則會發生在事件之後。|
|建議|以 .NET Framework 4.7.1 或更新版本為目標的應用程式可透過在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列內容來選擇退出此變更，並使用舊版行為：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以 .NET Framework 4.7 或舊版為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式，只要在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段新增下列程式行，就能啟用新行為：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

