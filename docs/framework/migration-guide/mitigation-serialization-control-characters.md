---
title: 使用 DataContractJsonSerializer 序列化控制字元
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452626"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>緩和：使用 DataContractJsonSerializer 將控制字元序列化

從 .NET Framework 4.7 開始，使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化控制字元的方式已變更，以符合 ECMAScript V6 和 V8。 
 
## <a name="impact"></a>影響

在 .NET Framework 4.6.2 和舊版中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 不會將某些特殊控制字元（例如 `\b`、`\f`和 `\t`）序列化為與 ECMAScript V6 和 V8 標準相容的方式。

對於以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，這些控制字元的序列化會與 ECMAScript V6 和 V8 相容。 以下是受影響的 API：

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>降低

對於以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，預設會啟用此行為。

如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
