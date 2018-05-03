### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x 依預設會將 SCH_SEND_AUX_RECORD 旗標傳遞至基礎的 SCHANNEL API

|   |   |
|---|---|
|詳細資料|使用 TLS 1.x 時，.NET Framework 依賴基礎的 Windows SCHANNEL API。 從 .NET Framework 4.6 開始，預設會傳遞 [SCH_SEND_AUX_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) 旗標給 SCHANNL。 這會導致 SCHANNEL 分割資料，以便加密成兩個不同的記錄，第一個是單一位元組，第二個則是 <em>n</em>-1 個位元組。在罕見的情況下，這會中斷用戶端與假設資料位於單一記錄中的現有伺服器之間的通訊。|
|建議|如果這項變更會中斷與現有伺服器的通訊，您可以停用傳送 [SCH_SEND_AUX_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) 旗標，並還原先前的行為，不將資料分割成個別的記錄，其方法是新增下列參數到應用程式設定檔 [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 中的 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] 提供此設定的目的，只是為了回溯相容性。 不建議用於其他用途。</blockquote> |
|範圍|Edge|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

