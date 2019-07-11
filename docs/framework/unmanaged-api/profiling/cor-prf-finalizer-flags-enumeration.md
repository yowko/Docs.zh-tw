---
title: COR_PRF_FINALIZER_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a66b2b94765c3d59327e500f1e208dc93cd8e231
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781926"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="4af3e-102">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4af3e-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="4af3e-103">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="4af3e-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4af3e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4af3e-105">成員</span><span class="sxs-lookup"><span data-stu-id="4af3e-105">Members</span></span>  
  
|<span data-ttu-id="4af3e-106">成員</span><span class="sxs-lookup"><span data-stu-id="4af3e-106">Member</span></span>|<span data-ttu-id="4af3e-107">描述</span><span class="sxs-lookup"><span data-stu-id="4af3e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="4af3e-108">完成項非常重要。</span><span class="sxs-lookup"><span data-stu-id="4af3e-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4af3e-109">備註</span><span class="sxs-lookup"><span data-stu-id="4af3e-109">Remarks</span></span>  
 <span data-ttu-id="4af3e-110">`COR_PRF_FINALIZER_FLAGS`列舉由[ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)方法來描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="4af3e-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af3e-111">需求</span><span class="sxs-lookup"><span data-stu-id="4af3e-111">Requirements</span></span>  
 <span data-ttu-id="4af3e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4af3e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af3e-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4af3e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4af3e-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4af3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4af3e-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4af3e-116">See also</span></span>

- [<span data-ttu-id="4af3e-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="4af3e-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
