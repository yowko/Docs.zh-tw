---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614373"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer 的控制字元序列化現在與 ECMAScript V6 和 V8 相容

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 和舊版中，並未 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> 以與 ECMAScript V6 和 V8 標準相容的方式序列化某些特殊控制字元，例如 \b、\f 和 \t。 從 .NET Framework 4.7 開始，這些控制字元的序列化會與 ECMAScript V6 和 V8 相容。

#### <a name="suggestion"></a>建議

若為以 .NET Framework 4.7 為目標的應用程式，會預設啟用此功能。 如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
