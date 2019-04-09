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
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123756"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="385aa-102">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="385aa-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="385aa-103">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="385aa-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="385aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="385aa-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="385aa-105">成員</span><span class="sxs-lookup"><span data-stu-id="385aa-105">Members</span></span>  
  
|<span data-ttu-id="385aa-106">成員</span><span class="sxs-lookup"><span data-stu-id="385aa-106">Member</span></span>|<span data-ttu-id="385aa-107">描述</span><span class="sxs-lookup"><span data-stu-id="385aa-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="385aa-108">完成項非常重要。</span><span class="sxs-lookup"><span data-stu-id="385aa-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="385aa-109">備註</span><span class="sxs-lookup"><span data-stu-id="385aa-109">Remarks</span></span>  
 <span data-ttu-id="385aa-110">`COR_PRF_FINALIZER_FLAGS`列舉由[ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)方法來描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="385aa-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="385aa-111">需求</span><span class="sxs-lookup"><span data-stu-id="385aa-111">Requirements</span></span>  
 <span data-ttu-id="385aa-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="385aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="385aa-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="385aa-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="385aa-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="385aa-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="385aa-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="385aa-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="385aa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="385aa-116">See also</span></span>

- [<span data-ttu-id="385aa-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="385aa-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
