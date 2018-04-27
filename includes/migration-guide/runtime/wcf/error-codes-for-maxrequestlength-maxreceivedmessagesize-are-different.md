### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>maxRequestLength 或 maxReceivedMessageSize 的錯誤碼不同

|   |   |
|---|---|
|詳細資料|Internet Information Services (IIS) 或 ASP.NET 程式開發伺服器裝載的 WCF Web 服務中，超過 maxRequestLength (在 ASP.NET 中) 或 maxReceivedMessageSize (在 WCF 中) 的訊息具有不同的錯誤碼。HTTP 狀態碼已從 400 (錯誤的要求) 變更為 413 (要求的實體太大)，而且超過 maxRequestLength 或 maxReceivedMessageSize 設定的訊息會擲回 <xref:System.ServiceModel.ProtocolException?displayProperty=name> 例外狀況。 傳輸模式為 Streamed 的案例也包括在內。|
|建議|這項變更有助於在訊息長度超過 ASP.NET 或 WCF 所允許之限制的情況下進行偵錯。您必須修改任何依據 HTTP 400 狀態碼執行處理的程式碼。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|

