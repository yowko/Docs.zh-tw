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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b7a4c8dfc9e082b29d462b835886d6bf252bb39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753674"
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="baac9-102">COR_PRF_GC_ROOT_KIND 列舉</span><span class="sxs-lookup"><span data-stu-id="baac9-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="baac9-103">表示，由記憶體回收根目錄的種類[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="baac9-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baac9-104">語法</span><span class="sxs-lookup"><span data-stu-id="baac9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="baac9-105">成員</span><span class="sxs-lookup"><span data-stu-id="baac9-105">Members</span></span>  
  
|<span data-ttu-id="baac9-106">成員</span><span class="sxs-lookup"><span data-stu-id="baac9-106">Member</span></span>|<span data-ttu-id="baac9-107">說明</span><span class="sxs-lookup"><span data-stu-id="baac9-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="baac9-108">根目錄是在堆疊上的變數。</span><span class="sxs-lookup"><span data-stu-id="baac9-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="baac9-109">根是完成項佇列中的項目。</span><span class="sxs-lookup"><span data-stu-id="baac9-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="baac9-110">根是記憶體回收控制代碼。</span><span class="sxs-lookup"><span data-stu-id="baac9-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="baac9-111">未指定的根類型。</span><span class="sxs-lookup"><span data-stu-id="baac9-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="baac9-112">需求</span><span class="sxs-lookup"><span data-stu-id="baac9-112">Requirements</span></span>  
 <span data-ttu-id="baac9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baac9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baac9-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="baac9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="baac9-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baac9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baac9-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baac9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baac9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baac9-117">See also</span></span>

- [<span data-ttu-id="baac9-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="baac9-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
