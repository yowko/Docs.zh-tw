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
ms.openlocfilehash: a4c875f6aae996271dee9ac193768ef6981efc19
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863032"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="435ef-102">ICorProfilerInfo10：： SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="435ef-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="435ef-103">暫停執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="435ef-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="435ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="435ef-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="435ef-105">需求</span><span class="sxs-lookup"><span data-stu-id="435ef-105">Requirements</span></span>

<span data-ttu-id="435ef-106">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="435ef-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="435ef-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="435ef-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="435ef-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="435ef-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="435ef-109">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="435ef-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="435ef-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="435ef-110">See also</span></span>

- [<span data-ttu-id="435ef-111">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="435ef-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
