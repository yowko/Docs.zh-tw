---
title: SYSLIB0005 警告
description: 瞭解產生編譯時期警告 SYSLIB0005 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596475"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="8dc37-103">SYSLIB0005：不支援全域組件快取 (GAC) </span><span class="sxs-lookup"><span data-stu-id="8dc37-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="8dc37-104">.NET Core 和 .NET 5.0 和更新版本消除了 .NET Framework 中存在的全域組件快取 (GAC) 的概念。</span><span class="sxs-lookup"><span data-stu-id="8dc37-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="8dc37-105">為了協助開發人員遠離這些 Api，部分 GAC 相關的 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="8dc37-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="8dc37-106">使用這些 Api `SYSLIB0005` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="8dc37-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="8dc37-107">下列與 GAC 相關的 Api 已標示為過時：</span><span class="sxs-lookup"><span data-stu-id="8dc37-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="8dc37-108">程式庫和應用程式不應使用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> API 來判斷執行時間行為，因為它一律會 `false` 在 .net Core 和 .net 5 + 中傳回。</span><span class="sxs-lookup"><span data-stu-id="8dc37-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="8dc37-109">因應措施</span><span class="sxs-lookup"><span data-stu-id="8dc37-109">Workarounds</span></span>

<span data-ttu-id="8dc37-110">如果您的應用程式會查詢 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性，請考慮移除呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dc37-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="8dc37-111">如果您在 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 執行時間使用值來選擇「gac 中的元件」-flow 與「不在 gac 中的元件」的流程，請重新考慮流程是否仍然適合 .net 5 + 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dc37-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="8dc37-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dc37-112">See also</span></span>

- [<span data-ttu-id="8dc37-113">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="8dc37-113">Global assembly cache</span></span>](../../../framework/app-domains/gac.md)
