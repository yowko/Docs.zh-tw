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
ms.openlocfilehash: bff45e6f6f57b95d07ac5073cb70020818cce000
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867161"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="bb83c-102">COR_PRF_GC_ROOT_KIND 列舉</span><span class="sxs-lookup"><span data-stu-id="bb83c-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="bb83c-103">表示[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)回呼所公開的垃圾收集根目錄種類。</span><span class="sxs-lookup"><span data-stu-id="bb83c-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb83c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb83c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="bb83c-105">Members</span><span class="sxs-lookup"><span data-stu-id="bb83c-105">Members</span></span>  
  
|<span data-ttu-id="bb83c-106">成員</span><span class="sxs-lookup"><span data-stu-id="bb83c-106">Member</span></span>|<span data-ttu-id="bb83c-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb83c-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="bb83c-108">根是堆疊上的變數。</span><span class="sxs-lookup"><span data-stu-id="bb83c-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="bb83c-109">根是完成項佇列中的專案。</span><span class="sxs-lookup"><span data-stu-id="bb83c-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="bb83c-110">根是垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="bb83c-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="bb83c-111">未指定根類型。</span><span class="sxs-lookup"><span data-stu-id="bb83c-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb83c-112">需求</span><span class="sxs-lookup"><span data-stu-id="bb83c-112">Requirements</span></span>  
 <span data-ttu-id="bb83c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb83c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb83c-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb83c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb83c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb83c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb83c-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb83c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb83c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb83c-117">See also</span></span>

- [<span data-ttu-id="bb83c-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="bb83c-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
