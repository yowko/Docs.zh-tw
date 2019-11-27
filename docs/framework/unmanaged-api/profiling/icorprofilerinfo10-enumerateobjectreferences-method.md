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
ms.openlocfilehash: d6518612c213d21c2dc7d80878121ccd3b7e2abb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449847"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="f2186-102">ICorProfilerInfo10：： EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="f2186-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="f2186-103">假設有 ObjectID、callback 和 clientData，會列舉每個物件參考（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="f2186-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="f2186-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2186-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="f2186-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2186-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="f2186-106">在要列舉參考的物件。</span><span class="sxs-lookup"><span data-stu-id="f2186-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="f2186-107">在將使用物件的參考所呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="f2186-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="f2186-108">在分析工具提供的資料，以傳遞至 `callback` 函數。</span><span class="sxs-lookup"><span data-stu-id="f2186-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2186-109">備註</span><span class="sxs-lookup"><span data-stu-id="f2186-109">Remarks</span></span>

<span data-ttu-id="f2186-110">`EnumerateObjectReferences` 方法類似于[ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)，不同之處在于它會針對分析工具依照需求來進行參考，而不是預先配置陣列來儲存參考。</span><span class="sxs-lookup"><span data-stu-id="f2186-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2186-111">需求</span><span class="sxs-lookup"><span data-stu-id="f2186-111">Requirements</span></span>

<span data-ttu-id="f2186-112">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="f2186-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="f2186-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2186-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f2186-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2186-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f2186-115">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2186-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f2186-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2186-116">See also</span></span>

- [<span data-ttu-id="f2186-117">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="f2186-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
