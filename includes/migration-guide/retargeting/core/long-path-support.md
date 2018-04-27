### <a name="long-path-support"></a>長路徑支援

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6.2 為目標的應用程式開始，支援長路徑 (最多 32K 個字元)，且已移除對於路徑長度的 260 個字元 (或 <code>MAX_PATH</code>) 限制。若為重新編譯以 .NET Framework 4.6.2 為目標的應用程式，先前因為路徑超過 260 個字元而擲回 <xref:System.IO.PathTooLongException?displayProperty=name> 的程式碼路徑，現在將只有在下列情況下擲回 <xref:System.IO.PathTooLongException?displayProperty=name>：<ul><li>路徑的長度大於 <xref:System.Int16.MaxValue> (32,767) 個字元。</li><li>作業系統傳回 <code>COR_E_PATHTOOLONG</code> 或其對應項。</li></ul>若為以 .NET Framework 4.6.1 和更早版本為目標的應用程式，每當路徑超過 260 個字元時，執行階段就會自動擲回 <xref:System.IO.PathTooLongException?displayProperty=name>。|
|建議|若為以 .NET Framework 4.6.2 為目標的應用程式，如果不需要長路徑支援，您可以透過將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段以選擇退出長路徑支援︰<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.6.2 或更新版本上執行的應用程式，則可將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段，以選擇加入長路徑支援：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6.2|
|類型|正在重定目標|

