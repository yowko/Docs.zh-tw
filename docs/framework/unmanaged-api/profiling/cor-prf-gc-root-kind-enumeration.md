---
title: COR_PRF_GC_ROOT_KIND 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: e86074031b8fc2c82636e7aef2177eaf04a9db14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682360"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="6e00b-102">COR_PRF_GC_ROOT_KIND 列舉</span><span class="sxs-lookup"><span data-stu-id="6e00b-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>

<span data-ttu-id="6e00b-103">指出 [ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md) 回呼所公開的垃圾收集根類型。</span><span class="sxs-lookup"><span data-stu-id="6e00b-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e00b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e00b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="6e00b-105">成員</span><span class="sxs-lookup"><span data-stu-id="6e00b-105">Members</span></span>  
  
|<span data-ttu-id="6e00b-106">member</span><span class="sxs-lookup"><span data-stu-id="6e00b-106">Member</span></span>|<span data-ttu-id="6e00b-107">描述</span><span class="sxs-lookup"><span data-stu-id="6e00b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="6e00b-108">根是堆疊上的變數。</span><span class="sxs-lookup"><span data-stu-id="6e00b-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="6e00b-109">根是完成項佇列中的專案。</span><span class="sxs-lookup"><span data-stu-id="6e00b-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="6e00b-110">根是垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="6e00b-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="6e00b-111">未指定根類型。</span><span class="sxs-lookup"><span data-stu-id="6e00b-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e00b-112">需求</span><span class="sxs-lookup"><span data-stu-id="6e00b-112">Requirements</span></span>  

 <span data-ttu-id="6e00b-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e00b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e00b-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e00b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e00b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e00b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e00b-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e00b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e00b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e00b-117">See also</span></span>

- [<span data-ttu-id="6e00b-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="6e00b-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
