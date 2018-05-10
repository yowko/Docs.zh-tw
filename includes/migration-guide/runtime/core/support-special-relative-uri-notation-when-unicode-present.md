### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode 存在時，支援特殊的相對 URI 標記法

|   |   |
|---|---|
|詳細資料|在包含 Unicode 的某些相對 URI 上呼叫 <xref:System.Uri.TryCreate%2A> 時，<xref:System.Uri> 不會再擲回 <xref:System.NullReferenceException>。下面是重現 <xref:System.NullReferenceException> 最簡單的方式，使用相對等的兩個陳述式：<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>若要重現 <xref:System.NullReferenceException>，必須符合下列項目：<ul><li>URI 前面必須加上 ‘http:’，且不是後面加上 ‘//’ 來指定為相對的。</li><li>URI 必須包含百分比編碼的 Unicode 或未保留的符號。</li></ul>|
|建議|根據此行為不允許相對 URI 的使用者，在建立 URI 時應該改指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。|
|範圍|Edge|
|版本|4.7.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

