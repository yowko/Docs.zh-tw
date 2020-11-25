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
ms.openlocfilehash: 747313f217092652d5a9404fbf81383fa0828ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696657"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="ce3c8-102">COR_PRF_TRANSITION_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="ce3c8-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>

<span data-ttu-id="ce3c8-103">指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce3c8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="ce3c8-105">成員</span><span class="sxs-lookup"><span data-stu-id="ce3c8-105">Members</span></span>  
  
|<span data-ttu-id="ce3c8-106">member</span><span class="sxs-lookup"><span data-stu-id="ce3c8-106">Member</span></span>|<span data-ttu-id="ce3c8-107">描述</span><span class="sxs-lookup"><span data-stu-id="ce3c8-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="ce3c8-108">轉換是因為呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="ce3c8-109">轉換是因為函數傳回。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce3c8-110">備註</span><span class="sxs-lookup"><span data-stu-id="ce3c8-110">Remarks</span></span>  

 <span data-ttu-id="ce3c8-111">進行轉換時，分析工具會收到 [ICorProfilerCallback：： ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) 或 [ICorProfilerCallback：： UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) 回呼，其中任一個都提供列舉的值， `COR_PRF_TRANSITION_REASON` 以指出轉換的原因。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce3c8-112">需求</span><span class="sxs-lookup"><span data-stu-id="ce3c8-112">Requirements</span></span>  

 <span data-ttu-id="ce3c8-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce3c8-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce3c8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce3c8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce3c8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce3c8-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
