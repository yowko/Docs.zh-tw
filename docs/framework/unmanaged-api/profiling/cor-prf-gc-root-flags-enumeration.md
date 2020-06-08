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
ms.openlocfilehash: bbc163c71b47e6fee0db89284d6e3fd27e882768
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500880"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="38cde-102">COR_PRF_GC_ROOT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="38cde-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="38cde-103">表示垃圾收集根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="38cde-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38cde-104">語法</span><span class="sxs-lookup"><span data-stu-id="38cde-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="38cde-105">成員</span><span class="sxs-lookup"><span data-stu-id="38cde-105">Members</span></span>  
  
|<span data-ttu-id="38cde-106">成員</span><span class="sxs-lookup"><span data-stu-id="38cde-106">Member</span></span>|<span data-ttu-id="38cde-107">說明</span><span class="sxs-lookup"><span data-stu-id="38cde-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="38cde-108">根會防止垃圾收集移動物件。</span><span class="sxs-lookup"><span data-stu-id="38cde-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="38cde-109">根不會防止垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="38cde-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="38cde-110">根是指物件的欄位，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="38cde-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="38cde-111">如果物件的參考計數是特定值，則根目錄會防止垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="38cde-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38cde-112">備註</span><span class="sxs-lookup"><span data-stu-id="38cde-112">Remarks</span></span>  
 <span data-ttu-id="38cde-113">`COR_PRF_GC_ROOT_FLAGS`是一個位元遮罩，可提供特殊根的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="38cde-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="38cde-114">不過，並非所有的根都是特殊的。</span><span class="sxs-lookup"><span data-stu-id="38cde-114">However, not all roots are special.</span></span> <span data-ttu-id="38cde-115">例如，某些根不是弱式參考、內部指標、固定或參考計數。</span><span class="sxs-lookup"><span data-stu-id="38cde-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="38cde-116">對於這類根，沒有可傳達的旗標。</span><span class="sxs-lookup"><span data-stu-id="38cde-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="38cde-117">因此，使用這個列舉的方法（例如[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)方法）會傳送0做為旗標位元遮罩，表示所有旗標都已關閉。</span><span class="sxs-lookup"><span data-stu-id="38cde-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38cde-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="38cde-118">Requirements</span></span>  
 <span data-ttu-id="38cde-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38cde-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38cde-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38cde-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38cde-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38cde-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38cde-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38cde-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38cde-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38cde-123">See also</span></span>

- [<span data-ttu-id="38cde-124">分析列舉</span><span class="sxs-lookup"><span data-stu-id="38cde-124">Profiling Enumerations</span></span>](profiling-enumerations.md)
