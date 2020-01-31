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
ms.openlocfilehash: a443332e4f2b0351e99754fae610af39268bb105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789274"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="f5594-102">CorDebugSetContextFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="f5594-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="f5594-103">指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。</span><span class="sxs-lookup"><span data-stu-id="f5594-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5594-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5594-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="f5594-105">Members</span><span class="sxs-lookup"><span data-stu-id="f5594-105">Members</span></span>  
  
|<span data-ttu-id="f5594-106">成員</span><span class="sxs-lookup"><span data-stu-id="f5594-106">Member</span></span>|<span data-ttu-id="f5594-107">描述</span><span class="sxs-lookup"><span data-stu-id="f5594-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f5594-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="f5594-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="f5594-109">內容是執行緒的現用內容。</span><span class="sxs-lookup"><span data-stu-id="f5594-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="f5594-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="f5594-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="f5594-111">已從另一個框架回溯來計算內容。</span><span class="sxs-lookup"><span data-stu-id="f5594-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5594-112">備註</span><span class="sxs-lookup"><span data-stu-id="f5594-112">Remarks</span></span>  
 <span data-ttu-id="f5594-113">`CorDebugSetContextFlag` 提供[ICorDebugStackWalk：： SetCoNtext](icordebugstackwalk-setcontext-method.md)方法所使用的值。</span><span class="sxs-lookup"><span data-stu-id="f5594-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5594-114">需求</span><span class="sxs-lookup"><span data-stu-id="f5594-114">Requirements</span></span>  
 <span data-ttu-id="f5594-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5594-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5594-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5594-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5594-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5594-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5594-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5594-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5594-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5594-119">See also</span></span>

- [<span data-ttu-id="f5594-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f5594-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f5594-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="f5594-121">Debugging</span></span>](index.md)
