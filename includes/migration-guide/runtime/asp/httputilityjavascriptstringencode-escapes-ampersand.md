### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode 會逸出 & 符號

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> 會逸出 &amp; 字元。|
|建議|如果您的應用程式相依於此方法的舊版行為，您可以將 aspnet:JavaScriptDoNotEncodeAmpersand 設定新增至組態檔中的 [ASP.NET appSettings 項目](https://msdn.microsoft.com/library/hh975440.aspx)。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

