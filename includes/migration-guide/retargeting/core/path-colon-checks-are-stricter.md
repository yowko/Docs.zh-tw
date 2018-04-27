### <a name="path-colon-checks-are-stricter"></a>路徑冒號檢查更嚴格

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。 對於適當磁碟機分隔符號 (冒號) 語法的檢查更為正確，副作用則是會封鎖一些選取路徑 API 中的某些 URI 路徑，而在過去都會容許它們。|
|建議|如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。<ul><li>以手動方式從 URL 移除配置 (例如從 URL 移除 <code>file://</code>)</li><li>將 URI 傳遞給 <xref:System.Uri> 類別，並且使用 <xref:System.Uri.LocalPath></li></ul>或者，將 <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext 參數設為 true，以選擇退出新的路徑正規化。|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

