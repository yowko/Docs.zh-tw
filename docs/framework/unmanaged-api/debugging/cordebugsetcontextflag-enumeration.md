---
title: "CorDebugSetContextFlag 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27e9fd561da74a3b88015e7820c2cbbd56ab2a7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="5b278-102">CorDebugSetContextFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="5b278-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="5b278-103">指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。</span><span class="sxs-lookup"><span data-stu-id="5b278-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b278-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b278-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="5b278-105">成員</span><span class="sxs-lookup"><span data-stu-id="5b278-105">Members</span></span>  
  
|<span data-ttu-id="5b278-106">成員</span><span class="sxs-lookup"><span data-stu-id="5b278-106">Member</span></span>|<span data-ttu-id="5b278-107">描述</span><span class="sxs-lookup"><span data-stu-id="5b278-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5b278-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="5b278-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="5b278-109">內容是在執行緒的作用中的內容。</span><span class="sxs-lookup"><span data-stu-id="5b278-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="5b278-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="5b278-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="5b278-111">內容已經過計算，藉由從其他框架回溯。</span><span class="sxs-lookup"><span data-stu-id="5b278-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b278-112">備註</span><span class="sxs-lookup"><span data-stu-id="5b278-112">Remarks</span></span>  
 <span data-ttu-id="5b278-113">`CorDebugSetContextFlag`提供值，可供[icordebugstackwalk:: Setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5b278-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b278-114">需求</span><span class="sxs-lookup"><span data-stu-id="5b278-114">Requirements</span></span>  
 <span data-ttu-id="5b278-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b278-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b278-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b278-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b278-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b278-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b278-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b278-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b278-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b278-119">See Also</span></span>  
 [<span data-ttu-id="5b278-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5b278-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="5b278-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="5b278-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
