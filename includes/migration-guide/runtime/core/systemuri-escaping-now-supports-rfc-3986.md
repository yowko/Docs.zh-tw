### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.URI 逸出現在支援 RFC 3986

|   |   |
|---|---|
|詳細資料|URI 逸出在 .NET 4.5 中已變更，可支援 [RFC 3986](http://tools.ietf.org/html/rfc3986)。 特定變更包括：<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> 會根據 RFC 3986 逸出保留字元。</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> 不會逸出保留字元。</li><li>如果 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> 遇到無效的逸出序列，則不會擲回例外狀況。</li><li>非保留的逸出字元不逸出。</li></ul>|
|建議|<ul><li>請更新應用程式，以便在逸出序列無效時，不依賴 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> 擲回例外狀況。 現在必須直接偵測這類序列。</li><li>同樣地，逸出和未逸出 URI 以及資料字串可能會因 .NET 4.0 和 .NET 4.5 而有所不同，因此不應該在不同的 .NET 版本之間直接進行比較。 相反地，應該將這些字串剖析和正規化為單一 .NET 版本，再進行任何比較。</li></ul>|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

