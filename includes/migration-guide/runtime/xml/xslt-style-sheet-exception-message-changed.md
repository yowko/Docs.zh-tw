### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT 樣式表例外狀況訊息已變更

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，當 XSLT 檔太複雜時，錯誤訊息的文字會是「樣式表太複雜」在舊版中，錯誤訊息是「XSLT 編譯錯誤」倚賴錯誤訊息文字的應用程式程式碼將無法運作。 不過，例外狀況類型會保持不變，因此這項變更應該不會產生實際影響。|
|建議|請將依據此錯誤狀況之例外狀況訊息的任何應用程式程式碼更新為預期會有新訊息，或是 (甚至更佳的做法) 將程式碼更新為只依據尚未變更的例外狀況類型 (<xref:System.Xml.Xsl.XsltException?displayProperty=name>)。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

