### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision 和 DbParameter.Scale 現在是公用虛擬成員

|   |   |
|---|---|
|詳細資料|<xref:System.Data.Common.DbParameter.Precision> 和 <xref:System.Data.Common.DbParameter.Scale> 會當做公用虛擬屬性來實作。 這些屬性取代對應的明確介面實作 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。|
|建議|重建 ADO.NET 資料庫提供者時，這些差異會要求將 'override' 關鍵字套用至 Precision 和 Scale 屬性。 只有在重建元件時才需要這樣做；現有的二進位檔將繼續運作。|
|範圍|次要|
|版本|4.5.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

