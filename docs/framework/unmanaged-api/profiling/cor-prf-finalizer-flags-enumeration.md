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
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867265"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="c9f57-102">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="c9f57-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="c9f57-103">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="c9f57-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f57-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9f57-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c9f57-105">Members</span><span class="sxs-lookup"><span data-stu-id="c9f57-105">Members</span></span>  
  
|<span data-ttu-id="c9f57-106">成員</span><span class="sxs-lookup"><span data-stu-id="c9f57-106">Member</span></span>|<span data-ttu-id="c9f57-107">描述</span><span class="sxs-lookup"><span data-stu-id="c9f57-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="c9f57-108">完成項很重要。</span><span class="sxs-lookup"><span data-stu-id="c9f57-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9f57-109">備註</span><span class="sxs-lookup"><span data-stu-id="c9f57-109">Remarks</span></span>  
 <span data-ttu-id="c9f57-110">[ICorProfilerCallback2：： FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md)方法會使用 `COR_PRF_FINALIZER_FLAGS` 列舉來描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="c9f57-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f57-111">需求</span><span class="sxs-lookup"><span data-stu-id="c9f57-111">Requirements</span></span>  
 <span data-ttu-id="c9f57-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f57-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f57-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9f57-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9f57-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9f57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9f57-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f57-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f57-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f57-116">See also</span></span>

- [<span data-ttu-id="c9f57-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="c9f57-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
