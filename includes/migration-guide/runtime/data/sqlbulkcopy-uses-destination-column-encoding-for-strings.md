### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy 針對字串使用目的地資料行編碼方式

|   |   |
|---|---|
|詳細資料|將資料插入資料行時，<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> 會使用目的地資料行的編碼方式，而不是 <code>VARCHAR</code> 和 <code>CHAR</code> 類型的預設編碼方式。 這項變更可排除當目的地資料行未使用預設編碼方式時，使用預設編碼方式可能造成的資料損毀。 在某些鮮少發生的情況下，如果變更編碼方式後產生的資料太大而不適用於目的地資料行，現有的應用程式可能會擲回 SqlException 例外狀況。|
|建議|由於編碼方式的差異，預期 <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> 不會再損毀資料。 如果所複製的字串接近目的地資料行的大小限制，可能必須預先編碼資料 (要複製以確認資料可納入目的地資料行) 或攔截 <xref:System.Data.SqlClient.SqlException?displayProperty=name>。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|

