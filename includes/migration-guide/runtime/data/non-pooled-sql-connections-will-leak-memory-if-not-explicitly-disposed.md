### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>如果未明確處置，則非共用 SQL 連線將會造成記憶體流失

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，未明確處置 (透過 Dispose、Close 或 using) 的非共用 SQL 連線將會流失記憶體|
|建議|此問題是在 .NET Framework 4.5 服務更新中進行修正。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。 或者，在 &#39;using&#39; 模式中使用 <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> (這是最佳做法)，或不再需要連線時明確地呼叫 Dispose 或 Close，可能會避免此問題。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

