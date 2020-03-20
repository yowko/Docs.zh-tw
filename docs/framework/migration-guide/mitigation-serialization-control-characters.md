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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="6beac-102">緩解：使用資料合同Jon序列化器對控制字元進行序列化</span><span class="sxs-lookup"><span data-stu-id="6beac-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="6beac-103">從 .NET 框架 4.7 開始，使用 序列化控制項字元的方式<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>已更改為符合 ECMAScript V6 和 V8。</span><span class="sxs-lookup"><span data-stu-id="6beac-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="6beac-104">影響</span><span class="sxs-lookup"><span data-stu-id="6beac-104">Impact</span></span>

<span data-ttu-id="6beac-105">在 .NET Framework 4.6.2 和<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>早期版本中，未以與 ECMAScript `\b`V6 和 V8 標準相容的方式序列化某些特殊控制字元，例如 ，`\f`和`\t`，</span><span class="sxs-lookup"><span data-stu-id="6beac-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="6beac-106">對於以 .NET 框架 4.7 開頭的目標版本的應用，這些控制字元的序列化與 ECMAScript V6 和 V8 相容。</span><span class="sxs-lookup"><span data-stu-id="6beac-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="6beac-107">以下是受影響的 API：</span><span class="sxs-lookup"><span data-stu-id="6beac-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="6beac-108">降低</span><span class="sxs-lookup"><span data-stu-id="6beac-108">Mitigation</span></span>

<span data-ttu-id="6beac-109">對於以 .NET 框架 4.7 開頭的目標版本的 .NET Framework 的應用，預設情況下將啟用此行為。</span><span class="sxs-lookup"><span data-stu-id="6beac-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="6beac-110">如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：</span><span class="sxs-lookup"><span data-stu-id="6beac-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="6beac-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6beac-111">See also</span></span>

- [<span data-ttu-id="6beac-112">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="6beac-112">Application compatibility</span></span>](application-compatibility.md)
