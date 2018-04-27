### <a name="certificate-eku-oid-validation"></a>憑證 EKU OID 驗證

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6 開始，<xref:System.Net.Security.SslStream> 或 <xref:System.Net.ServicePointManager> 類別會執行增強金鑰使用方法 (EKU) 物件識別碼 (OID) 驗證。 增強金鑰使用方法 (EKU) 延伸模組是表示使用金鑰之應用程式的物件識別碼 (OID) 集合。 EKU OID 驗證會使用遠端憑證回呼，以確保遠端憑證有用於預定目的的正確 OID。|
|建議|如果不需要這項變更，您可以在程式應用程式設定檔的 [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 新增下列參數到 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，停用憑證 EKU OID 驗證：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] 提供此設定的目的，只是為了回溯相容性。 不建議用於其他用途。</blockquote> |
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

