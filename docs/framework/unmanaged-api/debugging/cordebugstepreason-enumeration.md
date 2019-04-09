---
title: CorDebugStepReason 列舉
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186247"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="8248b-102">CorDebugStepReason 列舉</span><span class="sxs-lookup"><span data-stu-id="8248b-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="8248b-103">指出個別步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="8248b-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8248b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8248b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="8248b-105">成員</span><span class="sxs-lookup"><span data-stu-id="8248b-105">Members</span></span>  
  
|<span data-ttu-id="8248b-106">成員</span><span class="sxs-lookup"><span data-stu-id="8248b-106">Member</span></span>|<span data-ttu-id="8248b-107">描述</span><span class="sxs-lookup"><span data-stu-id="8248b-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="8248b-108">逐步執行正常，完成相同的函式內。</span><span class="sxs-lookup"><span data-stu-id="8248b-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="8248b-109">逐步執行正常繼續進行之後的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="8248b-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="8248b-110">逐步執行正常繼續進行，在新的呼叫的函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="8248b-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="8248b-111">產生例外狀況和控制項傳遞至例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="8248b-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="8248b-112">產生例外狀況和控制項傳遞至例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="8248b-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="8248b-113">控制項傳遞至攔截器。</span><span class="sxs-lookup"><span data-stu-id="8248b-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="8248b-114">執行緒結束之前已完成該步驟。</span><span class="sxs-lookup"><span data-stu-id="8248b-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8248b-115">需求</span><span class="sxs-lookup"><span data-stu-id="8248b-115">Requirements</span></span>  
 <span data-ttu-id="8248b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8248b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8248b-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8248b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8248b-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8248b-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8248b-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8248b-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8248b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8248b-120">See also</span></span>

- [<span data-ttu-id="8248b-121">StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="8248b-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="8248b-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="8248b-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
