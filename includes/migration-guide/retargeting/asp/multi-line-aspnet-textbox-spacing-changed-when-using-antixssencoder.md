### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>使用 AntiXSSEncoder 時，多行 ASP.Net TextBox 間距已變更

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.0 中，如果使用 <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>，則會在回傳時，於多行文字方塊的行間插入額外幾行。 在 .NET Framework 4.5 中，不會包含這些額外的分行符號，但前提是 Web 應用程式是以 .NET 4.5 為目標|
|建議|請注意，重定目標為 .NET 4.5 的 4.0 版 Web 應用程式可能已改進多行文字方塊，不再插入額外的分行符號。 如果不想這麼做，在 .NET Framework 4.5 上執行的應用程式可藉由將目標設為 .NET Framework 4.0 來保留舊版行為。|
|範圍|次要|
|版本|4.5|
|類型|正在重定目標|

