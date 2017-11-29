---
title: "CorDebugIntercept 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7d34b5f1bdff7a7089d780645b91503a8464849
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="27788-102">CorDebugIntercept 列舉</span><span class="sxs-lookup"><span data-stu-id="27788-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="27788-103">表示可以攔截這類型的程式碼 (也就是逐步執行)。</span><span class="sxs-lookup"><span data-stu-id="27788-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27788-104">語法</span><span class="sxs-lookup"><span data-stu-id="27788-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="27788-105">成員</span><span class="sxs-lookup"><span data-stu-id="27788-105">Members</span></span>  
  
|<span data-ttu-id="27788-106">成員</span><span class="sxs-lookup"><span data-stu-id="27788-106">Member</span></span>|<span data-ttu-id="27788-107">說明</span><span class="sxs-lookup"><span data-stu-id="27788-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="27788-108">無法攔截任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="27788-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="27788-109">可以攔截建構函式。</span><span class="sxs-lookup"><span data-stu-id="27788-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="27788-110">可以攔截例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="27788-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="27788-111">可以攔截會強制執行安全性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="27788-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="27788-112">可以攔截內容原則。</span><span class="sxs-lookup"><span data-stu-id="27788-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="27788-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="27788-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="27788-114">可以攔截所有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="27788-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27788-115">備註</span><span class="sxs-lookup"><span data-stu-id="27788-115">Remarks</span></span>  
 <span data-ttu-id="27788-116">使用[icordebugstepper:: Setinterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)方法，以建立可以攔截的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="27788-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27788-117">需求</span><span class="sxs-lookup"><span data-stu-id="27788-117">Requirements</span></span>  
 <span data-ttu-id="27788-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27788-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27788-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27788-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27788-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27788-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27788-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27788-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27788-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27788-122">See Also</span></span>  
 [<span data-ttu-id="27788-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="27788-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
