### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter 可能無法從 LoadFrom 內容尋找類型

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> 將已在 LoadFrom 內容中載入的類型還原序列化時，<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> 變更可能會造成還原序列化的差異。 這些變更是由於新方法 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> 現在會載入類型，因此這會在 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> 稍後嘗試為該類型還原序列化時，導致不同的行為。 預設序列化繫結器不會自動搜尋 LoadFrom 內容，雖然在某些狀況下，其根據 XmlSerializer 舊有行為可正常運作。 由於這些變更之故，從在不同內容載入的組件中載入類型時，可能會擲回 <xref:System.IO.FileNotFoundException?displayProperty=name>。|
|建議|如果看到這個例外狀況，<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> 的 <code>Binder</code> 屬性可以設定為自訂繫結器，用來尋找正確的類型。<pre><code class="language-C#">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>然後，自訂繫結器：<pre><code class="language-C#">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

