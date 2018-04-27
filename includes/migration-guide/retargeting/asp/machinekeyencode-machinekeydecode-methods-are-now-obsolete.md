### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode 和 MachineKey.Decode 方法現在已淘汰

|   |   |
|---|---|
|詳細資料|這些方法現在已經過時。 編譯呼叫這些方法的程式碼會產生編譯器警告。|
|建議|建議的替代方式為 <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> 和 <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>。 或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。 這些 API 仍受到支援。|
|範圍|次要|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

