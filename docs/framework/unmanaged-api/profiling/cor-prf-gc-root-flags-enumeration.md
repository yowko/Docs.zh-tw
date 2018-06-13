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
ms.openlocfilehash: 2d5dcb089074b52fc87a0bb83c7e062e7ef07b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450397"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="45fe7-102">COR_PRF_GC_ROOT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="45fe7-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="45fe7-103">指出記憶體回收根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="45fe7-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45fe7-104">語法</span><span class="sxs-lookup"><span data-stu-id="45fe7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="45fe7-105">成員</span><span class="sxs-lookup"><span data-stu-id="45fe7-105">Members</span></span>  
  
|<span data-ttu-id="45fe7-106">成員</span><span class="sxs-lookup"><span data-stu-id="45fe7-106">Member</span></span>|<span data-ttu-id="45fe7-107">描述</span><span class="sxs-lookup"><span data-stu-id="45fe7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="45fe7-108">根會防止記憶體回收移動物件。</span><span class="sxs-lookup"><span data-stu-id="45fe7-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="45fe7-109">根目錄不會防止記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="45fe7-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="45fe7-110">根參考了欄位的物件，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="45fe7-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="45fe7-111">根物件的參考計數是否為某個值，可防止記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="45fe7-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45fe7-112">備註</span><span class="sxs-lookup"><span data-stu-id="45fe7-112">Remarks</span></span>  
 <span data-ttu-id="45fe7-113">`COR_PRF_GC_ROOT_FLAGS` 是提供特殊的根物件的其他資訊的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="45fe7-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="45fe7-114">不過，並非所有的根 ca 是特殊的。</span><span class="sxs-lookup"><span data-stu-id="45fe7-114">However, not all roots are special.</span></span> <span data-ttu-id="45fe7-115">例如，某些根不是弱式參考，已釘選，或參考計數的內部指標。</span><span class="sxs-lookup"><span data-stu-id="45fe7-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="45fe7-116">這類的根目錄中，有任何旗標來傳遞。</span><span class="sxs-lookup"><span data-stu-id="45fe7-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="45fe7-117">因此，方法使用這個列舉型別，例如[icorprofilercallback2:: Rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法時，send 0 旗標位元遮罩，指出所有旗標已關閉。</span><span class="sxs-lookup"><span data-stu-id="45fe7-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45fe7-118">需求</span><span class="sxs-lookup"><span data-stu-id="45fe7-118">Requirements</span></span>  
 <span data-ttu-id="45fe7-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45fe7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45fe7-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45fe7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45fe7-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45fe7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45fe7-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45fe7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fe7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45fe7-123">See Also</span></span>  
 [<span data-ttu-id="45fe7-124">分析列舉</span><span class="sxs-lookup"><span data-stu-id="45fe7-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
