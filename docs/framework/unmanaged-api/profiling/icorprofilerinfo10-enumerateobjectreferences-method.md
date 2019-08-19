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
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974028"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="97f34-102">ICorProfilerInfo10:: EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="97f34-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>
  
 <span data-ttu-id="97f34-103">假設有 ObjectID、callback 和 clientData, 會列舉每個物件參考 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="97f34-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="97f34-104">語法</span><span class="sxs-lookup"><span data-stu-id="97f34-104">Syntax</span></span>  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a><span data-ttu-id="97f34-105">參數</span><span class="sxs-lookup"><span data-stu-id="97f34-105">Parameters</span></span>  

 `objectId` \
 <span data-ttu-id="97f34-106">在要列舉參考的物件。</span><span class="sxs-lookup"><span data-stu-id="97f34-106">[in] The object to enumerate references on.</span></span>

 `callback` \
 <span data-ttu-id="97f34-107">在將使用物件的參考所呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="97f34-107">[in] The function that will be called with the references for the object.</span></span>

 `clientData` \
 <span data-ttu-id="97f34-108">在要傳遞至`callback`函式的 Profiler 提供資料。</span><span class="sxs-lookup"><span data-stu-id="97f34-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="97f34-109">備註</span><span class="sxs-lookup"><span data-stu-id="97f34-109">Remarks</span></span>  
 <span data-ttu-id="97f34-110">`EnumerateObjectReferences`方法類似于 [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), 不同之處在于它會針對分析工具依照需求來進行參考, 而不是預先配置陣列來儲存參考。</span><span class="sxs-lookup"><span data-stu-id="97f34-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>  

## <a name="requirements"></a><span data-ttu-id="97f34-111">需求</span><span class="sxs-lookup"><span data-stu-id="97f34-111">Requirements</span></span>  
 <span data-ttu-id="97f34-112">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="97f34-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="97f34-113">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="97f34-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97f34-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97f34-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97f34-115">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97f34-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97f34-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f34-116">See also</span></span>
- [<span data-ttu-id="97f34-117">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="97f34-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

