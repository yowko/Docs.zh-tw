### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> 物件)。 嘗試序列化 MEF 目錄會擲回例外狀況。|
|建議|無法再使用 MEF 建立序列化程式|
|範圍|主要|
|版本|4.5|
|類型|執行階段|

