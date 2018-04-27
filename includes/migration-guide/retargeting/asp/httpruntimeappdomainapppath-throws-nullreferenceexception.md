### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath 擲回 NullReferenceException

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 中，執行階段在擷取包含 null 字元的 <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> 值時，會擲回 <code>T:System.NullReferenceException</code>。在 .NET Framework 4.6.1 和更早版本中，執行階段會擲回 <code>T:System.ArgumentNullException</code>。|
|建議|您可以執行下列其中一個動作以回應這項變更︰<ul><li>如果您的應用程式是在 .NET Framework 4.6.2 上執行，請處理 <code>T:System.NullReferenceException</code>。</li><li>升級至 .NET Framework 4.7，這可以還原舊版行為並擲回 <code>T:System.ArgumentNullException</code>。</li></ul>|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

