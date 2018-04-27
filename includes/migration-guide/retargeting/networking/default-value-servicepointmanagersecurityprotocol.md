### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager.SecurityProtocol 的預設值是 SecurityProtocolType.System.Default

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.7 為目標的應用程式開始，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性是 <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>。 這項變更可以讓以 SslStream 為基礎的 .NET Framework 網路 API (例如 FTP、HTTPS 及 SMTP) 繼承作業系統的預設安全性通訊協定，而不要使用由 .NET Framework 定義的硬式編碼值。 預設值會依作業系統和系統管理員執行的任何自訂設定而異。 如需每個 Windows 作業系統版本中的預設安全通道通訊協定的資訊，請參閱 [TLS/SSL 中的通訊協定 (安全通道 SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159.aspx)。若為以舊版 .NET Framework 為目標的應用程式，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性的預設值會依目標 .NET Framework 版本而定。 如需詳細資訊，請參閱[從 .NET Framework 4.5.2 移轉到 4.6 的重定目標變更的網路區段](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)。|
|建議|這項變更會影響以 .NET Framework 4.7 或更新版本為目標的應用程式。如果您想要使用定義的通訊協定，而不是依賴系統預設值，您可以明確設定 <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性的值。如果不需要這項變更，您可以藉由新增組態設定至應用程式設定檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇不使用它。 下列範例顯示 <code>&lt;runtime&gt;</code> 區段及 <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> 選擇退出參數：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

