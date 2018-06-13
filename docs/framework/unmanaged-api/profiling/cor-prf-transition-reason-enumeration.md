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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450059"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="6819b-102">COR_PRF_TRANSITION_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="6819b-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="6819b-103">指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。</span><span class="sxs-lookup"><span data-stu-id="6819b-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6819b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6819b-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="6819b-105">成員</span><span class="sxs-lookup"><span data-stu-id="6819b-105">Members</span></span>  
  
|<span data-ttu-id="6819b-106">成員</span><span class="sxs-lookup"><span data-stu-id="6819b-106">Member</span></span>|<span data-ttu-id="6819b-107">描述</span><span class="sxs-lookup"><span data-stu-id="6819b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="6819b-108">轉換是因為呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="6819b-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="6819b-109">轉換是因為從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="6819b-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6819b-110">備註</span><span class="sxs-lookup"><span data-stu-id="6819b-110">Remarks</span></span>  
 <span data-ttu-id="6819b-111">轉換發生時，分析工具收到[icorprofilercallback:: Managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)或[icorprofilercallback:: Unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)回呼，而提供的值`COR_PRF_TRANSITION_REASON`列舉型別以表示轉換的原因。</span><span class="sxs-lookup"><span data-stu-id="6819b-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6819b-112">需求</span><span class="sxs-lookup"><span data-stu-id="6819b-112">Requirements</span></span>  
 <span data-ttu-id="6819b-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6819b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6819b-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6819b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6819b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6819b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6819b-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6819b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
