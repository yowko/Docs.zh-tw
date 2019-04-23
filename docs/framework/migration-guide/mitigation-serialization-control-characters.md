---
title: 風險降低：使用 DataContractJsonSerializer 將控制字元序列化
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182113"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>風險降低：使用 DataContractJsonSerializer 將控制字元序列化

從 .NET Framework 4.7 開始，使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化控制字元的方式已變更為符合 ECMAScript V6 和 V8。 
 
## <a name="impact"></a>影響

在 .NET framework 4.6.2 和舊版中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 不會以相容於 ECMAScript V6 及 V8 標準的方式序列化某些特殊控制字元，例如 `\b`、`\f` 和 `\t`。

對於以從 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，序列化這些控制字元的方式已相容於 ECMAScript V6 和 V8。 以下是受影響的 API：

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>緩和

對於以 .NET Framework 4.7 版開始的 .NET Framework 為目標的應用程式，此行為預設為啟用。

如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>另請參閱

- [.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
