---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: a3dca2cbb138dbc43f477488032e67335c8b15f9
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452158"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="c3d45-102">ICorProfilerInfo10：： ResumeRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="c3d45-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="c3d45-103">繼續執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="c3d45-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3d45-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3d45-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="c3d45-105">需求</span><span class="sxs-lookup"><span data-stu-id="c3d45-105">Requirements</span></span>

<span data-ttu-id="c3d45-106">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="c3d45-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="c3d45-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3d45-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c3d45-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3d45-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c3d45-109">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d45-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c3d45-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3d45-110">See also</span></span>

- [<span data-ttu-id="c3d45-111">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="c3d45-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
