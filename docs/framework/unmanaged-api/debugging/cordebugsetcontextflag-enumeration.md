---
title: CorDebugSetContextFlag 列舉
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e959ce7a77ad6ceb7f2fc848193cbd9fff028279
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739614"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="ac270-102">CorDebugSetContextFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="ac270-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="ac270-103">指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。</span><span class="sxs-lookup"><span data-stu-id="ac270-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac270-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac270-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="ac270-105">成員</span><span class="sxs-lookup"><span data-stu-id="ac270-105">Members</span></span>  
  
|<span data-ttu-id="ac270-106">成員</span><span class="sxs-lookup"><span data-stu-id="ac270-106">Member</span></span>|<span data-ttu-id="ac270-107">說明</span><span class="sxs-lookup"><span data-stu-id="ac270-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ac270-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="ac270-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="ac270-109">內容是執行緒的作用中的內容。</span><span class="sxs-lookup"><span data-stu-id="ac270-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="ac270-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="ac270-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="ac270-111">已藉由從其他框架回溯計算內容。</span><span class="sxs-lookup"><span data-stu-id="ac270-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac270-112">備註</span><span class="sxs-lookup"><span data-stu-id="ac270-112">Remarks</span></span>  
 <span data-ttu-id="ac270-113">`CorDebugSetContextFlag` 提供值，可供[icordebugstackwalk:: Setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ac270-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac270-114">需求</span><span class="sxs-lookup"><span data-stu-id="ac270-114">Requirements</span></span>  
 <span data-ttu-id="ac270-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac270-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac270-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac270-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac270-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac270-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac270-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac270-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac270-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac270-119">See also</span></span>

- [<span data-ttu-id="ac270-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ac270-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="ac270-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="ac270-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
