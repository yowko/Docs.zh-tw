### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>在 System.Net.ServicePointManager 和 System.Net.Security.SslStream 只支援 Tls 1.0、1.1 及 1.2 通訊協定

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6 開始，只有 <xref:System.Net.ServicePointManager> 和 <xref:System.Net.Security.SslStream> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。 不支援 SSL3.0 通訊協定與 RC4 編碼器。|
|建議|建議的緩和措施是將伺服器端應用程式升級至 Tls1.0、Tls1.1 或 Tls1.2。 如果這並不可行，或是用戶端應用程式已中斷，則可使用 <xref:System.AppContext?displayProperty=name> 類別搭配下列兩種方式之一，停用這項功能：<ol><li>以程式設計方式設定 <xref:System.AppContext?displayProperty=name> 的相容性參數，如[這裡](http://blogs.msdn.com/b/dotnet/archive/2015/04/29/net-announcements-at-build-2015.aspx#dotnet46)所述</li><li>將下行新增至 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段：<code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code>；</li></ol>|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

