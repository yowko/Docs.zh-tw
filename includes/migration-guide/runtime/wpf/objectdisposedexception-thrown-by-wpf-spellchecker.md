### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>WPF 拼字檢查功能所擲回的 ObjectDisposedException

|   |   |
|---|---|
|詳細資料|在應用程式關閉期間，WPF 應用程式偶爾會因拼字檢查功能所擲回的 <xref:System.ObjectDisposedException?displayProperty=name> 而損毀。 此問題已在 .NET 4.7 WPF 中透過依正常程序處理例外狀況來修正，進而確保應用程式不會再受到負面影響。 請注意，在偵錯工具下執行的應用程式偶爾還是會發生第一個例外狀況。|
|建議|升級至 .NET 4.7|
|範圍|Edge|
|版本|4.6.1|
|類型|執行階段|

