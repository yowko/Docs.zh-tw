---
title: "風險降低︰使用 DataContractJsonSerializer 序列化控制字元 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 596d7ea858e40a558767fa76bb717dbbba97d4ed
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>風險降低︰使用 DataContractJsonSerializer 序列化控制字元

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
 
## <a name="see-also"></a>請參閱
[.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

