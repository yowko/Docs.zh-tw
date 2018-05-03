### <a name="wcf-services-that-use-nettcp-with-ssl-sercurity-and-md5-certificate-authentication"></a>使用 NETTCP 進行 SSL 安全性和 MD5 憑證驗證的 WCF 服務

|   |   |
|---|---|
|詳細資料|.NET Framework 4.6 新增了 TLS 1.1 和 TLS 1.2 至 WCF SSL 的預設通訊協定清單。 當用戶端和伺服器電腦安裝 .NET Framework 4.6 或更新版本時，會使用 TLS 1.2 進行交涉。TLS 1.2 不支援 MD5 憑證驗證。 因此，如果客戶使用 MD5 憑證，WCF 用戶端將無法連線到 WCF 服務。<ul><li>[ ] Quirked // 使用某個機制來開啟或關閉功能，通常使用執行階段目標、AppContext 或組態檔。 在某些情況下，需要自動予以開啟。</li><li>[ ] 建置階段中斷 // 如果嘗試重新編譯，則會導致中斷</li></ul>|
|建議|您可以執行下列其中一項動作來解決這個問題，使 WCF 用戶端可以連線到 WCF 伺服器︰<ul><li>更新憑證為不使用 MD5 演算法。 這是建議的解決方案。</li><li>如果繫結在原始程式碼中不是以動態方式設定，請更新應用程式的組態檔，以使用 TLS 1.1 或舊版的通訊協定。 這可讓您繼續使用執行 MD5 雜湊演算法的憑證。</li></ul>
<blockquote>
[!WARNING] 我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</blockquote>
下列組態檔示範如何進行：<pre><code>&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None|Transport|Message|TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None|Windows|Certificate&quot;&#13;&#10;protectionLevel=&quot;None|Sign|EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3|Tls1|Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>如果繫結在原始程式碼中是以動態方式設定，請更新 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> 屬性，以在原始程式碼中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或舊版的通訊協定。</li></ul>
<blockquote>
[!WARNING] 我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</blockquote>| |範圍|未知| |版本|4.6| |型別|執行階段|

