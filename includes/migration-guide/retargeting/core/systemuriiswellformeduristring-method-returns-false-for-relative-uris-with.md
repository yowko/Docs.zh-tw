### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>System.Uri.IsWellFormedUriString 方法針對第一個區段中有冒號字元的相對 URI 會傳回 false

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> 會將第一個區段中具有 <code>:</code> 的相對 URI 視為格式不正確。 這是 .NET Framework 4.0 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> 行為的變更，以符合 RFC3986。|
|建議|這項變更 (就像許多其他的 URI 變更一樣) 只會影響以 .NET Framework 4.5 (或更新版本) 為目標的應用程式。 若要繼續使用舊的行為，請將應用程式設為以 .NET Framework 4.0 為目標。 或者，在呼叫 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> 前掃描 URI，尋找 <code>:</code> 字元，如果您偏好舊的行為，則請移除字元以進行驗證。|
|範圍|次要|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

