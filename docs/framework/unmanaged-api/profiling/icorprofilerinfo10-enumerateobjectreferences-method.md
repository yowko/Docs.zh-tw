---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: a276ecfe65ed9752f39ed68a36e8e17a24255508
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558312"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="4bd7d-102">ICorProfilerInfo10：： EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="4bd7d-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="4bd7d-103">如果有 ObjectID，回呼和 clientData 會列舉每個物件參考 (是否有任何) 。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="4bd7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bd7d-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="4bd7d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4bd7d-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="4bd7d-106">\[in] 要列舉參考的物件。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="4bd7d-107">\[in] 將以物件的參考呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="4bd7d-108">\[in] 要傳遞給函式的 Profiler 提供資料 `callback` 。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bd7d-109">備註</span><span class="sxs-lookup"><span data-stu-id="4bd7d-109">Remarks</span></span>

<span data-ttu-id="4bd7d-110">`EnumerateObjectReferences`方法類似于[ObjectReferences](icorprofilercallback-objectreferences-method.md)，不同之處在于它會針對分析工具進行隨選參考，而不是預先配置陣列來儲存參考。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bd7d-111">需求</span><span class="sxs-lookup"><span data-stu-id="4bd7d-111">Requirements</span></span>

<span data-ttu-id="4bd7d-112">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="4bd7d-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="4bd7d-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4bd7d-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="4bd7d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bd7d-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="4bd7d-115">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd7d-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4bd7d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd7d-116">See also</span></span>

- [<span data-ttu-id="4bd7d-117">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="4bd7d-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
