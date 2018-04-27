### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>某些 .NET API 會造成第一個可能發生 (已處理) 的 EntryPointNotFoundException

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，少數 .NET 方法已開始擲回第一個可能發生的 <xref:System.EntryPointNotFoundException?displayProperty=name>。 這些例外狀況在 .Net Framework 中已處理，但可能會中斷未預期第一個可能發生例外狀況的測試自動化。 這些相同的 API 會在啟用 HighVersionLie 時中斷一些 ApiVerifier 案例。|
|建議|您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。 或者，您也可以更新測試自動化，不要在發生第一個可能的 <xref:System.EntryPointNotFoundException?displayProperty=name> 時中斷。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

