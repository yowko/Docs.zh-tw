### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>AesCryptoServiceProvider 解密程式提供可重複使用的轉換

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6.2 為目標的應用程式開始，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密程式會提供可重複使用的轉換。 呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> 之後，轉換就會重新初始化並且可重複使用。 若為以舊版 .NET Framework 為目標的應用程式，嘗試透過在呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> 之後呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> 來重複使用解密程式，會擲回 <xref:System.Security.Cryptography.CryptographicException> 或產生損毀的資料。|
|建議|此變更的影響應該很小，因為這是預期的行為。倚賴舊行為的應用程式可以藉由將下列組態設定新增到應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段，選擇不使用：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>此外，以舊版 .NET Framework 為目標，但是在從 .NET Framework 4.6.2 開始的 .NET Framework 版本下執行的應用程式，可以藉由將下列組態設定新增到應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段，來選擇使用：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|

