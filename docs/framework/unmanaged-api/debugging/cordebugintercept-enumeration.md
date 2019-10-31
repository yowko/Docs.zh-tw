---
title: CorDebugIntercept 列舉
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 144bdb1b4e479c1e75f89911ad5002e2650e405d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098115"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="b0f7e-102">CorDebugIntercept 列舉</span><span class="sxs-lookup"><span data-stu-id="b0f7e-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="b0f7e-103">表示可以攔截這類型的程式碼 (也就是逐步執行)。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0f7e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b0f7e-105">Members</span><span class="sxs-lookup"><span data-stu-id="b0f7e-105">Members</span></span>  
  
|<span data-ttu-id="b0f7e-106">成員</span><span class="sxs-lookup"><span data-stu-id="b0f7e-106">Member</span></span>|<span data-ttu-id="b0f7e-107">描述</span><span class="sxs-lookup"><span data-stu-id="b0f7e-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="b0f7e-108">無法攔截任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="b0f7e-109">可以攔截建構函式。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="b0f7e-110">可以攔截例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="b0f7e-111">可以攔截會強制執行安全性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="b0f7e-112">可以攔截內容原則。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="b0f7e-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="b0f7e-114">可以攔截所有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0f7e-115">備註</span><span class="sxs-lookup"><span data-stu-id="b0f7e-115">Remarks</span></span>  
 <span data-ttu-id="b0f7e-116">請使用[ICorDebugStepper：： SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)方法來建立可攔截的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0f7e-117">需求</span><span class="sxs-lookup"><span data-stu-id="b0f7e-117">Requirements</span></span>  
 <span data-ttu-id="b0f7e-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0f7e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0f7e-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0f7e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0f7e-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0f7e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0f7e-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0f7e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f7e-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0f7e-122">See also</span></span>

- [<span data-ttu-id="b0f7e-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b0f7e-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
