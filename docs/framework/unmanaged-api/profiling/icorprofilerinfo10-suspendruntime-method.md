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
ms.openlocfilehash: 121ed0401628193f6e2fe632a124c08aad7bd1b4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551435"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="7e2a8-102">ICorProfilerInfo10：： SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="7e2a8-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="7e2a8-103">暫停執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="7e2a8-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e2a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e2a8-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="7e2a8-105">需求</span><span class="sxs-lookup"><span data-stu-id="7e2a8-105">Requirements</span></span>

<span data-ttu-id="7e2a8-106">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="7e2a8-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="7e2a8-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e2a8-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="7e2a8-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e2a8-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7e2a8-109">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2a8-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7e2a8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e2a8-110">See also</span></span>

- [<span data-ttu-id="7e2a8-111">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="7e2a8-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
