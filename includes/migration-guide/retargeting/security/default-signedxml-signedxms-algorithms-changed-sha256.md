### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>預設 SignedXML 和 SignedXMS 演算法變更為 SHA256

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7 和更早版本中，某些作業的 SignedXML 和 SignedCMS 預設為 SHA1。從 .NET Framework 4.7.1 開始，針對這些作業預設會啟用 SHA256。 這項變更是必要的，因為 SHA1 不再被視為是安全的方法。|
|建議|有兩個新內容參數值可以控制預設使用 SHA1 (不安全) 還是 SHA256：<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>若為以 .NET Framework 4.7.1 和更新版本為目標的應用程式，如果使用 SHA256 不適當，您可以將預設值還原為 SHA1 ，方法是新增下列設定參數到應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>若為以 .NET Framework 4.7.1 和更早版本為目標的應用程式，您可以新增下列設定參數到應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，選擇加入此變更：<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

