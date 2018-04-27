### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase 不會傳播 OnStart 例外狀況

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7 和更早版本中，在服務啟動時擲回的例外狀況不會傳播至 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> 的呼叫端。從 .NET Framework 4.7.1 為目標的應用程式開始，執行階段會為無法啟動的服務將例外狀況傳播到 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>。|
|建議|在服務啟動時，如果有例外狀況，將會傳播該例外狀況。 這應該有助於診斷服務無法啟動的情況。如果不需要這個行為，您可以新增下列 <AppContextSwitchOverrides> 項目至應用程式設定檔的 <runtime>區段，選擇不使用它：<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>如果您的應用程式以比 4.7.1 舊的版本為目標，但您想要有這種行為，請新增下列 <AppContextSwitchOverrides> 項目至應用程式設定檔的 <runtime> 區段：<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

