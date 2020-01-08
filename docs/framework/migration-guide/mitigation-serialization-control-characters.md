---
title: 使用 DataContractJsonSerializer 序列化控制字元
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346577"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="5e4cf-102">緩和：使用 DataContractJsonSerializer 將控制字元序列化</span><span class="sxs-lookup"><span data-stu-id="5e4cf-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="5e4cf-103">從 .NET Framework 4.7 開始，使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化控制字元的方式已變更為符合 ECMAScript V6 和 V8。</span><span class="sxs-lookup"><span data-stu-id="5e4cf-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="5e4cf-104">影響</span><span class="sxs-lookup"><span data-stu-id="5e4cf-104">Impact</span></span>

<span data-ttu-id="5e4cf-105">在 .NET framework 4.6.2 和舊版中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 不會以相容於 ECMAScript V6 及 V8 標準的方式序列化某些特殊控制字元，例如 `\b`、`\f` 和 `\t`。</span><span class="sxs-lookup"><span data-stu-id="5e4cf-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="5e4cf-106">對於以從 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，序列化這些控制字元的方式已相容於 ECMAScript V6 和 V8。</span><span class="sxs-lookup"><span data-stu-id="5e4cf-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="5e4cf-107">以下是受影響的 API：</span><span class="sxs-lookup"><span data-stu-id="5e4cf-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="5e4cf-108">風險降低</span><span class="sxs-lookup"><span data-stu-id="5e4cf-108">Mitigation</span></span>

<span data-ttu-id="5e4cf-109">對於以 .NET Framework 4.7 版開始的 .NET Framework 為目標的應用程式，此行為預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="5e4cf-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="5e4cf-110">如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：</span><span class="sxs-lookup"><span data-stu-id="5e4cf-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="5e4cf-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e4cf-111">See also</span></span>

- [<span data-ttu-id="5e4cf-112">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="5e4cf-112">Application compatibility</span></span>](application-compatibility.md)
