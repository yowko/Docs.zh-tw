---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465992"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer 的控制字元序列化現在與 ECMAScript V6 和 V8 相容

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 和舊版中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> 不會將某些特殊控制字元（例如 \b、\f 和 \t）序列化為與 ECMAScript V6 和 V8 標準相容的方式。 從 .NET Framework 4.7 開始，這些控制字元的序列化會與 ECMAScript V6 和 V8 相容。|
|建議|若為以 .NET Framework 4.7 為目標的應用程式，會預設啟用此功能。 如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 <code>&lt;runtime&gt;</code> 區段，以選擇退出此功能：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|影響範圍|Edge|
|版本|4.7|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
