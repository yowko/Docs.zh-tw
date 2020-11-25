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
ms.openlocfilehash: 2b766715d6d87ab17a7cdabf721bbebf67e1ff13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718575"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="feeb7-102">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="feeb7-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>

<span data-ttu-id="feeb7-103">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="feeb7-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feeb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="feeb7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="feeb7-105">成員</span><span class="sxs-lookup"><span data-stu-id="feeb7-105">Members</span></span>  
  
|<span data-ttu-id="feeb7-106">member</span><span class="sxs-lookup"><span data-stu-id="feeb7-106">Member</span></span>|<span data-ttu-id="feeb7-107">描述</span><span class="sxs-lookup"><span data-stu-id="feeb7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="feeb7-108">完成項相當重要。</span><span class="sxs-lookup"><span data-stu-id="feeb7-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feeb7-109">備註</span><span class="sxs-lookup"><span data-stu-id="feeb7-109">Remarks</span></span>  

 <span data-ttu-id="feeb7-110">`COR_PRF_FINALIZER_FLAGS` [ICorProfilerCallback2：： FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md)方法會使用列舉來描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="feeb7-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feeb7-111">需求</span><span class="sxs-lookup"><span data-stu-id="feeb7-111">Requirements</span></span>  

 <span data-ttu-id="feeb7-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="feeb7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feeb7-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="feeb7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="feeb7-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feeb7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feeb7-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feeb7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feeb7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feeb7-116">See also</span></span>

- [<span data-ttu-id="feeb7-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="feeb7-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
