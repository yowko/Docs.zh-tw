---
title: 使用資料合同序列器對控制字元進行序列化
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181203"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>緩解：使用資料合同Jon序列化器對控制字元進行序列化

從 .NET 框架 4.7 開始，使用 序列化控制項字元的方式<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>已更改為符合 ECMAScript V6 和 V8。

## <a name="impact"></a>影響

在 .NET Framework 4.6.2 和<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>早期版本中，未以與 ECMAScript `\b`V6 和 V8 標準相容的方式序列化某些特殊控制字元，例如 ，`\f`和`\t`，

對於以 .NET 框架 4.7 開頭的目標版本的應用，這些控制字元的序列化與 ECMAScript V6 和 V8 相容。 以下是受影響的 API：

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>降低

對於以 .NET 框架 4.7 開頭的目標版本的 .NET Framework 的應用，預設情況下將啟用此行為。

如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
