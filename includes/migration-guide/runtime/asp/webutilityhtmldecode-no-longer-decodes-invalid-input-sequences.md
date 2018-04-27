### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode 不再將無效的輸入序列解碼

|   |   |
|---|---|
|詳細資料|根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。|
|建議|解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|

