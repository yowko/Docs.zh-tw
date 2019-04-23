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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263c22a07f363c2752afb50779515de043976e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207704"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="dff8a-102">COR_PRF_GC_ROOT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="dff8a-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="dff8a-103">指出記憶體回收根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="dff8a-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dff8a-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="dff8a-105">成員</span><span class="sxs-lookup"><span data-stu-id="dff8a-105">Members</span></span>  
  
|<span data-ttu-id="dff8a-106">成員</span><span class="sxs-lookup"><span data-stu-id="dff8a-106">Member</span></span>|<span data-ttu-id="dff8a-107">描述</span><span class="sxs-lookup"><span data-stu-id="dff8a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="dff8a-108">根目錄會防止記憶體回收移動物件。</span><span class="sxs-lookup"><span data-stu-id="dff8a-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="dff8a-109">根目錄不會防止記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="dff8a-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="dff8a-110">根參考的物件，而不是物件本身的欄位。</span><span class="sxs-lookup"><span data-stu-id="dff8a-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="dff8a-111">根物件的參考計數是否為某個值，可防止記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="dff8a-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dff8a-112">備註</span><span class="sxs-lookup"><span data-stu-id="dff8a-112">Remarks</span></span>  
 <span data-ttu-id="dff8a-113">`COR_PRF_GC_ROOT_FLAGS` 會提供特殊的根憑證的其他資訊的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="dff8a-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="dff8a-114">不過，並非所有的根是特殊的。</span><span class="sxs-lookup"><span data-stu-id="dff8a-114">However, not all roots are special.</span></span> <span data-ttu-id="dff8a-115">比方說，有些根不是弱式參考，釘選，或參考計數的內部指標。</span><span class="sxs-lookup"><span data-stu-id="dff8a-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="dff8a-116">這類的根目錄中，有要傳達的任何旗標。</span><span class="sxs-lookup"><span data-stu-id="dff8a-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="dff8a-117">因此，使用這個列舉型別，例如的方法[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法，傳送 0 為旗標位元遮罩，指出所有旗標為關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="dff8a-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dff8a-118">需求</span><span class="sxs-lookup"><span data-stu-id="dff8a-118">Requirements</span></span>  
 <span data-ttu-id="dff8a-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dff8a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dff8a-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dff8a-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dff8a-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dff8a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dff8a-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dff8a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff8a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dff8a-123">See also</span></span>

- [<span data-ttu-id="dff8a-124">分析列舉</span><span class="sxs-lookup"><span data-stu-id="dff8a-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
