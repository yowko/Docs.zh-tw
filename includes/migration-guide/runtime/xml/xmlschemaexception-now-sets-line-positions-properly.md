### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException 現在會正確設定行位置

|   |   |
|---|---|
|詳細資料|如果將 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值傳遞至 Load 方法且發生驗證錯誤，則 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 屬性現在會包含行資訊。|
|建議|您應該更新假設不會設定 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的例外狀況處理程式碼，因為當使用 SetLineInfo 載入 XML 時，現在會正確設定這些屬性。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

