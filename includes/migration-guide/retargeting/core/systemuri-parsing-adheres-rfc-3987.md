### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>System.Uri 剖析遵守 RFC 3987

|   |   |
|---|---|
|詳細資料|URI 剖析在 .NET 4.5 中已做了幾項變更。 不過請注意，這些變更只會影響以 .NET 4.5 為目標的程式碼。 如果某個二進位檔是以 .NET 4.0 為目標，則會遵守舊版行為。 .NET 4.5 中的 URI 剖析變更包括：<ul><li>URI 剖析將會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查。</li><li>只會在 URI 的主機部分執行 Unicode 正規化格式 C。</li><li>無效的 mailto: URI 現在會造成例外狀況。</li><li>現在會保留路徑線段結尾的後置點。</li><li><code>file://</code> URI 不會逸出 <code>?</code> 字元。</li><li>不支援 Unicode 控制字元 <code>U+0080</code> 至 <code>U+009F</code>。</li><li>逗號字元 <code>,</code> 或 <code>%2c</code> 不會自動設為未逸出。</li></ul>|
|建議|如果需要舊版 .NET 4.0 URI 剖析語意 (通常不需要)，藉由設定 .NET 4.0 目標即可使用。 您可以在組件上使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>，或透過 Visual Studio 專案系統 UI 的 [專案屬性] 頁面來完成此作業。|
|範圍|主要|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|

