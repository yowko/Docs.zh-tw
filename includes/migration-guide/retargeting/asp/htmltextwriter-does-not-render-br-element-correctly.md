### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter 無法正確轉譯 `<br/>` 項目

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6 開始，使用 <code>&lt;BR /&gt;</code> 項目呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 將會正確地只插入一個 <code>&lt;BR /&gt;</code> (而不是兩個)|
|建議|如果應用程式需要額外的 <code>&lt;BR /&gt;</code> 標籤，則應該再次呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。 請注意，這項行為變更只會影響以 .NET Framework 4.6 或更新版本為目標的應用程式，因此另一個做法是以舊版 .NET Framework 為目標，以取得舊版行為。|
|範圍|Edge|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

