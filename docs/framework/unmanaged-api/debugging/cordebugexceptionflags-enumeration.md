---
title: CorDebugExceptionFlags 列舉
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 352a45a33a109570f100e91a24cd44dc4f6780e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740143"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="5648e-102">CorDebugExceptionFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="5648e-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="5648e-103">提供例外狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="5648e-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5648e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5648e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5648e-105">成員</span><span class="sxs-lookup"><span data-stu-id="5648e-105">Members</span></span>  
  
|<span data-ttu-id="5648e-106">成員</span><span class="sxs-lookup"><span data-stu-id="5648e-106">Member</span></span>|<span data-ttu-id="5648e-107">說明</span><span class="sxs-lookup"><span data-stu-id="5648e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="5648e-108">沒有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5648e-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="5648e-109">例外狀況為可攔截。</span><span class="sxs-lookup"><span data-stu-id="5648e-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="5648e-110">例外狀況可能仍處於偵錯工具無法攔截的時機。</span><span class="sxs-lookup"><span data-stu-id="5648e-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="5648e-111">例如，連結 Just-in-time (JIT) 所產生的目前回呼或例外狀況事件下沒有 Managed 程式碼時，則無法攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5648e-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5648e-112">備註</span><span class="sxs-lookup"><span data-stu-id="5648e-112">Remarks</span></span>  
 <span data-ttu-id="5648e-113">可能會在之後的版本中將新值加入至此列舉，因此您應該為未預期的值準備使用 `CorDebugExceptionFlags` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5648e-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5648e-114">需求</span><span class="sxs-lookup"><span data-stu-id="5648e-114">Requirements</span></span>  
 <span data-ttu-id="5648e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5648e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5648e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5648e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5648e-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5648e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5648e-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5648e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5648e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5648e-119">See also</span></span>

- [<span data-ttu-id="5648e-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5648e-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
