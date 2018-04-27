### <a name="resizing-a-grid-can-hang"></a>調整方格大小可能會當機

|   |   |
|---|---|
|詳細資料|在下列情況下，<code>T:System.Windows.Controls.Grid</code> 配置期間可能會發生無限迴圈：<ul><li>資料列定義包含兩個 *-row，這兩個都會宣告 MinHeigh 和 MaxHeight。</li><li>*-row 的內容不會超過對應的 MaxHeight</li><li>第一個 MinHeight (加上任何其他固定或自動的資料列) 超過方格的可用高度</li><li>應用程式將目標設為 .Net 4.7，或藉由設定 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 選擇加入 4.7 配置演算法</li></ul>有兩個以上的資料列時或在類似的資料行案例中也會發生此迴圈。此問題已在 .Net 4.7.1 中修正。|
|建議|升級至 .Net 4.7.1。  或者，如果您不需要 4.7 配置演算法，可以使用下列組態設定：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7|
|類型|執行階段|

