### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>WCF 傳輸安全性支援使用 CNG 儲存的憑證

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6.2 為目標的應用程式開始，WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。 這項支援僅限於具有公開金鑰的憑證，且指數長度不能超過 32 位元。 當應用程式以 .NET Framework 4.6.2 為目標時，此功能預設為開啟。在舊版 .NET Framework 中，嘗試搭配 CSG 金鑰儲存提供者使用 X509 憑證會擲回例外狀況。|
|建議|應用程式是以 .NET Framework 4.6.1 和更早版本為目標，但卻執行於 .NET Framework 4.6.2 當中，則可將下列這一行新增至 app.config 或 web.config 檔的 <code>&lt;runtime&gt;</code> 區段，來啟用支援 CNG 憑證：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>這也可以用程式設計方式，以下列程式碼完成︰<pre><code class="language-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="language-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>請注意，由於這項變更，將不再執行任何倚賴使用 CNG 憑證嘗試起始安全通訊失敗的任何例外住況處理程式碼。|
|範圍|次要|
|版本|4.6.2|
|類型|正在重定目標|

