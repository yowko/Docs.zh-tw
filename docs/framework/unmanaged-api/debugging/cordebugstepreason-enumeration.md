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
ms.openlocfilehash: 3d9dc94689083d79858319387747eb9dafe8b2f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739570"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="ad8d8-102">CorDebugStepReason 列舉</span><span class="sxs-lookup"><span data-stu-id="ad8d8-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="ad8d8-103">指出個別步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad8d8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="ad8d8-105">成員</span><span class="sxs-lookup"><span data-stu-id="ad8d8-105">Members</span></span>  
  
|<span data-ttu-id="ad8d8-106">成員</span><span class="sxs-lookup"><span data-stu-id="ad8d8-106">Member</span></span>|<span data-ttu-id="ad8d8-107">描述</span><span class="sxs-lookup"><span data-stu-id="ad8d8-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="ad8d8-108">逐步執行正常，完成相同的函式內。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="ad8d8-109">逐步執行正常繼續進行之後的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="ad8d8-110">逐步執行正常繼續進行，在新的呼叫的函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="ad8d8-111">產生例外狀況和控制項傳遞至例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="ad8d8-112">產生例外狀況和控制項傳遞至例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="ad8d8-113">控制項傳遞至攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="ad8d8-114">執行緒結束之前已完成該步驟。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad8d8-115">需求</span><span class="sxs-lookup"><span data-stu-id="ad8d8-115">Requirements</span></span>  
 <span data-ttu-id="ad8d8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8d8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad8d8-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad8d8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad8d8-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad8d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad8d8-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad8d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8d8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad8d8-120">See also</span></span>

- [<span data-ttu-id="ad8d8-121">StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="ad8d8-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="ad8d8-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ad8d8-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
