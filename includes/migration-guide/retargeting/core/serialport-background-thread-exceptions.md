### <a name="serialport-background-thread-exceptions"></a>SerialPort 背景執行緒例外狀況

|   |   |
|---|---|
|詳細資料|使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒不會再於 OS 擲回例外狀況時終止處理序。在以 .NET Framework 4.7 和更早版本為目標的應用程式中，當使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒擲回作業系統例外狀況時，會終止處理序。在以 .NET Framework 4.7.1 或更新版本為目標的應用程式中，背景執行緒會等候與作用中序列連接埠相關的 OS 事件，在某些情況下可能會損毀，例如突然移除序列連接埠。|
|建議|若為以 .NET Framework 4.7.1 為目標的應用程式，如果不需要例外狀況處理，您可以透過將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段以選擇退出例外狀況處理︰<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.1 或更新版本上執行的應用程式，則可將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段，以選擇加入例外狀況處理：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

