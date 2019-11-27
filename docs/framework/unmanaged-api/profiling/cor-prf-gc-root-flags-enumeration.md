---
title: COR_PRF_GC_ROOT_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 174486a88192bd5ff11074930d5ad3375603f8a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449466"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="3ab13-102">COR_PRF_GC_ROOT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="3ab13-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="3ab13-103">表示垃圾收集根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ab13-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab13-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ab13-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3ab13-105">Members</span><span class="sxs-lookup"><span data-stu-id="3ab13-105">Members</span></span>  
  
|<span data-ttu-id="3ab13-106">成員</span><span class="sxs-lookup"><span data-stu-id="3ab13-106">Member</span></span>|<span data-ttu-id="3ab13-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ab13-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="3ab13-108">根會防止垃圾收集移動物件。</span><span class="sxs-lookup"><span data-stu-id="3ab13-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="3ab13-109">根不會防止垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3ab13-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="3ab13-110">根是指物件的欄位，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="3ab13-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="3ab13-111">如果物件的參考計數是特定值，則根目錄會防止垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3ab13-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ab13-112">備註</span><span class="sxs-lookup"><span data-stu-id="3ab13-112">Remarks</span></span>  
 <span data-ttu-id="3ab13-113">`COR_PRF_GC_ROOT_FLAGS` 是一個位元遮罩，可提供特殊根的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ab13-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="3ab13-114">不過，並非所有的根都是特殊的。</span><span class="sxs-lookup"><span data-stu-id="3ab13-114">However, not all roots are special.</span></span> <span data-ttu-id="3ab13-115">例如，某些根不是弱式參考、內部指標、固定或參考計數。</span><span class="sxs-lookup"><span data-stu-id="3ab13-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="3ab13-116">對於這類根，沒有可傳達的旗標。</span><span class="sxs-lookup"><span data-stu-id="3ab13-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="3ab13-117">因此，使用這個列舉的方法（例如[ICorProfilerCallback2：： RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法）會傳送0做為旗標位元遮罩，表示所有旗標都已關閉。</span><span class="sxs-lookup"><span data-stu-id="3ab13-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab13-118">需求</span><span class="sxs-lookup"><span data-stu-id="3ab13-118">Requirements</span></span>  
 <span data-ttu-id="3ab13-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab13-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab13-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ab13-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ab13-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ab13-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ab13-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ab13-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab13-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ab13-123">See also</span></span>

- [<span data-ttu-id="3ab13-124">分析列舉</span><span class="sxs-lookup"><span data-stu-id="3ab13-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
