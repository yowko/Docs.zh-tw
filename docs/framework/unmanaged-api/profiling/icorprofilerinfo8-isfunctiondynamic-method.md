---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861732"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="e8860-102">ICorProfilerInfo8：： IsFunctionDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="e8860-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="e8860-103">判斷函數是否沒有相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e8860-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8860-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8860-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="e8860-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8860-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="e8860-106">\[in] 識別有問題之函式的 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="e8860-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="e8860-107">\[out] `BOOL` 的指標，其中會包含一個值，指出函數是否沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e8860-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8860-108">備註</span><span class="sxs-lookup"><span data-stu-id="e8860-108">Remarks</span></span>

<span data-ttu-id="e8860-109">如果函式沒有中繼資料，則會將其視為動態。</span><span class="sxs-lookup"><span data-stu-id="e8860-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="e8860-110">某些方法（例如 IL Stub 或 LCG 方法）沒有相關聯的中繼資料可使用 IMetaDataImport Api 來抓取。</span><span class="sxs-lookup"><span data-stu-id="e8860-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="e8860-111">分析工具可以透過指令指標或接聽[ICorProfilerCallback：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來發現這些方法。</span><span class="sxs-lookup"><span data-stu-id="e8860-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e8860-112">需求</span><span class="sxs-lookup"><span data-stu-id="e8860-112">Requirements</span></span>

<span data-ttu-id="e8860-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8860-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e8860-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8860-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e8860-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8860-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e8860-116">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8860-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8860-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8860-117">See also</span></span>

- [<span data-ttu-id="e8860-118">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="e8860-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
