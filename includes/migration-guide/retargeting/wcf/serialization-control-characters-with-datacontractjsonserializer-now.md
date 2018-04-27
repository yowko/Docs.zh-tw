### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer 的控制字元序列化現在與 ECMAScript V6 和 V8 相容

|   |   |
|---|---|
|詳細資料|在 .NET framework 4.6.2 和更早版本中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> 不會以相容於 ECMAScript V6 及 V8 標準的方式序列化某些特殊控制字元，例如 \b、\f 和 \t。 從 .NET Framework 4.7 開始，序列化這些控制字元的方式已相容於 ECMAScript V6 和 V8。|
|建議|若為以 .NET Framework 4.7 為目標的應用程式，會預設啟用此功能。 如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 <code>&lt;runtime&gt;</code> 區段，以選擇退出此功能：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

