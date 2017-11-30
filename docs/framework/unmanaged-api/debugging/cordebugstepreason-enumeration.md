---
title: "CorDebugStepReason 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32892a14de820e8add38654cef92aa44930aec62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="0569c-102">CorDebugStepReason 列舉</span><span class="sxs-lookup"><span data-stu-id="0569c-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="0569c-103">指出個別步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="0569c-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0569c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0569c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0569c-105">成員</span><span class="sxs-lookup"><span data-stu-id="0569c-105">Members</span></span>  
  
|<span data-ttu-id="0569c-106">成員</span><span class="sxs-lookup"><span data-stu-id="0569c-106">Member</span></span>|<span data-ttu-id="0569c-107">說明</span><span class="sxs-lookup"><span data-stu-id="0569c-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="0569c-108">逐步執行相同的函式內一般來說，完成。</span><span class="sxs-lookup"><span data-stu-id="0569c-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="0569c-109">逐步執行之後，繼續一般來說，此函式傳回。</span><span class="sxs-lookup"><span data-stu-id="0569c-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="0569c-110">逐步執行正常繼續進行，在新呼叫的函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="0569c-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="0569c-111">產生例外狀況，而且控制項已傳遞至例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="0569c-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="0569c-112">產生例外狀況，而且控制項已傳遞至例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="0569c-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="0569c-113">控制傳遞到攔截器。</span><span class="sxs-lookup"><span data-stu-id="0569c-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="0569c-114">執行緒結束之前完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="0569c-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0569c-115">需求</span><span class="sxs-lookup"><span data-stu-id="0569c-115">Requirements</span></span>  
 <span data-ttu-id="0569c-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0569c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0569c-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0569c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0569c-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0569c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0569c-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0569c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0569c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0569c-120">See Also</span></span>  
 [<span data-ttu-id="0569c-121">StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="0569c-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="0569c-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="0569c-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
