### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>將在 .NET Framework 4.5 下序列化的 MailMessage 物件還原序列化可能會失敗

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，<xref:System.Web.Mail.MailMessage> 物件可以包含非 ASCII 字元。 在 .NET Framework 4 中，僅支援 ASCII 字元。 包含非 ASCII 字元且在 .NET Framework 4.5 或更新版本下序列化的 <xref:System.Web.Mail.MailMessage> 物件，無法在 .NET Framework 4 下還原序列化。|
|建議|請確定您的程式碼在將 <xref:System.Web.Mail.MailMessage> 物件還原序列化時，會提供例外狀況處理。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

