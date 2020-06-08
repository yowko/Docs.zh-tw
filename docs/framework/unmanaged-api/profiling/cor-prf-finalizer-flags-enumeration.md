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
ms.openlocfilehash: b273faafd7abb86ace58bb5c24473406af3ce20e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500968"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="49280-102">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="49280-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="49280-103">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="49280-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49280-104">語法</span><span class="sxs-lookup"><span data-stu-id="49280-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="49280-105">成員</span><span class="sxs-lookup"><span data-stu-id="49280-105">Members</span></span>  
  
|<span data-ttu-id="49280-106">成員</span><span class="sxs-lookup"><span data-stu-id="49280-106">Member</span></span>|<span data-ttu-id="49280-107">說明</span><span class="sxs-lookup"><span data-stu-id="49280-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="49280-108">完成項很重要。</span><span class="sxs-lookup"><span data-stu-id="49280-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49280-109">備註</span><span class="sxs-lookup"><span data-stu-id="49280-109">Remarks</span></span>  
 <span data-ttu-id="49280-110">`COR_PRF_FINALIZER_FLAGS` [ICorProfilerCallback2：： FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md)方法會使用列舉型別來描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="49280-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49280-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="49280-111">Requirements</span></span>  
 <span data-ttu-id="49280-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49280-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49280-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49280-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49280-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49280-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49280-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49280-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49280-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49280-116">See also</span></span>

- [<span data-ttu-id="49280-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="49280-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
