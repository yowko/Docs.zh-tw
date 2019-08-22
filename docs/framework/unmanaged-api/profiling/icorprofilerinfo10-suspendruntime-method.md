---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 74300a12d000565a63cd7ea862c759d47b87bbe1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665702"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="56131-102">ICorProfilerInfo10:: SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="56131-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="56131-103">暫停執行時間, 而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="56131-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="56131-104">語法</span><span class="sxs-lookup"><span data-stu-id="56131-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="56131-105">需求</span><span class="sxs-lookup"><span data-stu-id="56131-105">Requirements</span></span>

<span data-ttu-id="56131-106">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="56131-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="56131-107">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="56131-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="56131-108">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56131-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="56131-109">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56131-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="56131-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56131-110">See also</span></span>

- [<span data-ttu-id="56131-111">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="56131-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
