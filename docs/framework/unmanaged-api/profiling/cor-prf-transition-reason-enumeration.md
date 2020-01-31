---
title: COR_PRF_TRANSITION_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867040"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="796a1-102">COR_PRF_TRANSITION_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="796a1-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="796a1-103">指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。</span><span class="sxs-lookup"><span data-stu-id="796a1-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="796a1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="796a1-105">Members</span><span class="sxs-lookup"><span data-stu-id="796a1-105">Members</span></span>  
  
|<span data-ttu-id="796a1-106">成員</span><span class="sxs-lookup"><span data-stu-id="796a1-106">Member</span></span>|<span data-ttu-id="796a1-107">描述</span><span class="sxs-lookup"><span data-stu-id="796a1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="796a1-108">轉換是因為函式的呼叫所造成。</span><span class="sxs-lookup"><span data-stu-id="796a1-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="796a1-109">轉換是因為從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="796a1-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="796a1-110">備註</span><span class="sxs-lookup"><span data-stu-id="796a1-110">Remarks</span></span>  
 <span data-ttu-id="796a1-111">當轉換發生時，分析工具會收到[ICorProfilerCallback：： ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md)或[ICorProfilerCallback：： UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md)回呼，其中任一項都會提供 `COR_PRF_TRANSITION_REASON` 列舉的值，以指出轉換的原因。</span><span class="sxs-lookup"><span data-stu-id="796a1-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796a1-112">需求</span><span class="sxs-lookup"><span data-stu-id="796a1-112">Requirements</span></span>  
 <span data-ttu-id="796a1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="796a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796a1-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="796a1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="796a1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="796a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="796a1-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796a1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
