### <a name="unicode-standard-version-80-categories-now-supported"></a>現在支援 Unicode 標準 8.0 版分類

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 中，Framework 的 Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。  在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。  這項變更主要會影響卻洛奇文音節和新傣文母音符號和音調標記。|
|建議|請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。|
|範圍|次要|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

