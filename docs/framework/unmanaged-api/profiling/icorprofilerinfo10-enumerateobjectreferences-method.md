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
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452236"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="f0b13-102">ICorProfilerInfo10：： EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="f0b13-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="f0b13-103">假設有 ObjectID、callback 和 clientData，會列舉每個物件參考（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="f0b13-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="f0b13-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0b13-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="f0b13-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0b13-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="f0b13-106">\[in] 要列舉參考的物件。</span><span class="sxs-lookup"><span data-stu-id="f0b13-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="f0b13-107">中的 \[] 使用物件的參考所呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="f0b13-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="f0b13-108">中的 \[] Profiler 提供的資料，以傳遞至 `callback` 函數。</span><span class="sxs-lookup"><span data-stu-id="f0b13-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0b13-109">備註</span><span class="sxs-lookup"><span data-stu-id="f0b13-109">Remarks</span></span>

<span data-ttu-id="f0b13-110">`EnumerateObjectReferences` 方法類似于[ObjectReferences](icorprofilercallback-objectreferences-method.md)，不同之處在于它會針對分析工具依照需求來進行參考，而不是預先配置陣列來儲存參考。</span><span class="sxs-lookup"><span data-stu-id="f0b13-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0b13-111">需求</span><span class="sxs-lookup"><span data-stu-id="f0b13-111">Requirements</span></span>

<span data-ttu-id="f0b13-112">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="f0b13-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="f0b13-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0b13-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f0b13-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0b13-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f0b13-115">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0b13-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f0b13-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b13-116">See also</span></span>

- [<span data-ttu-id="f0b13-117">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="f0b13-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
