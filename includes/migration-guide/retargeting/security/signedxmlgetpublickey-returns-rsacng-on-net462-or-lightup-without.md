### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey RSACng 會在 net462 (或 lightup) 上傳回 RSACng，而無重定目標變更

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6.2 開始，<xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> 方法所傳回的物件具象類型 (毫不奇怪地) 從 CryptoServiceProvider 實作變更為 Cng 實作。 這是因為實作從使用 <code>certificate.PublicKey.Key</code> 變更為使用內部 <code>certificate.GetAnyPublicKey</code>，它會轉送給 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>。|
|建議|從在 .NET Framework 4.7.1 上執行的應用程式開始，您可以使用 .NET Framework 4.6.1 和更早版本中預設使用的 CryptoServiceProvider 實作，方法是將下列設定參數新增至您應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

