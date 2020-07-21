---
title: 使用 DataContractJsonSerializer 序列化控制字元
description: 瞭解控制字元序列化在 .NET Framework 4.7 中，如何變更以符合 ECMAScript V6 和 V8 的方式。
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475381"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="a0b19-103">緩和：使用 DataContractJsonSerializer 將控制字元序列化</span><span class="sxs-lookup"><span data-stu-id="a0b19-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="a0b19-104">從 .NET Framework 4.7 開始，以序列化控制字元的方式 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 已變更為符合 ECMAScript V6 和 V8。</span><span class="sxs-lookup"><span data-stu-id="a0b19-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="a0b19-105">影響</span><span class="sxs-lookup"><span data-stu-id="a0b19-105">Impact</span></span>

<span data-ttu-id="a0b19-106">在 .NET Framework 4.6.2 和舊版中，並未 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化某些特殊控制字元，例如 `\b` 、 `\f` 和 `\t` ，其方式與 ECMAScript V6 和 V8 標準相容。</span><span class="sxs-lookup"><span data-stu-id="a0b19-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="a0b19-107">對於以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，這些控制字元的序列化會與 ECMAScript V6 和 V8 相容。</span><span class="sxs-lookup"><span data-stu-id="a0b19-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="a0b19-108">以下是受影響的 API：</span><span class="sxs-lookup"><span data-stu-id="a0b19-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="a0b19-109">降低</span><span class="sxs-lookup"><span data-stu-id="a0b19-109">Mitigation</span></span>

<span data-ttu-id="a0b19-110">對於以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式，預設會啟用此行為。</span><span class="sxs-lookup"><span data-stu-id="a0b19-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="a0b19-111">如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：</span><span class="sxs-lookup"><span data-stu-id="a0b19-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="a0b19-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b19-112">See also</span></span>

- [<span data-ttu-id="a0b19-113">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="a0b19-113">Application compatibility</span></span>](application-compatibility.md)
