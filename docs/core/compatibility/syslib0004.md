---
title: SYSLIB0004 警告
description: 瞭解產生編譯時期警告 SYSLIB0004 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ba7cd8a890a89000b241d286c9d8069ba1398849
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333246"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="1d8a3-103">SYSLIB0004：不支援 (CER) 功能的限制執列區域</span><span class="sxs-lookup"><span data-stu-id="1d8a3-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="1d8a3-104">只有在 .NET Framework 中才支援 [ (CER) 功能的受限制執列區域 ](../../framework/performance/constrained-execution-regions.md) 。</span><span class="sxs-lookup"><span data-stu-id="1d8a3-104">The [Constrained execution regions (CER)](../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="1d8a3-105">因此，從 .NET 5.0 開始，會將各種 CER 相關的 Api 標記為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="1d8a3-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="1d8a3-106">使用這些 Api `SYSLIB0004` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="1d8a3-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="1d8a3-107">下列 CER 相關的 Api 已淘汰：</span><span class="sxs-lookup"><span data-stu-id="1d8a3-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="1d8a3-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d8a3-108">See also</span></span>

- [<span data-ttu-id="1d8a3-109">限制的執列區域</span><span class="sxs-lookup"><span data-stu-id="1d8a3-109">Constrained execution regions</span></span>](../../framework/performance/constrained-execution-regions.md)
