### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm 預設值現在是 SHA256

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7.1 開始，WCF 中用於 Msmq 訊息的預設訊息簽署演算法是 SHA256。 在 .NET Framework 4.7 和舊版中，預設的訊息簽署演算法是 SHA1。|
|建議|如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|執行階段|

