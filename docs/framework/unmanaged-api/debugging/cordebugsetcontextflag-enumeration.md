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
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795673"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="fdf44-102">CorDebugSetContextFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="fdf44-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="fdf44-103">指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。</span><span class="sxs-lookup"><span data-stu-id="fdf44-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf44-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdf44-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="fdf44-105">成員</span><span class="sxs-lookup"><span data-stu-id="fdf44-105">Members</span></span>  
  
|<span data-ttu-id="fdf44-106">member</span><span class="sxs-lookup"><span data-stu-id="fdf44-106">Member</span></span>|<span data-ttu-id="fdf44-107">說明</span><span class="sxs-lookup"><span data-stu-id="fdf44-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fdf44-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="fdf44-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="fdf44-109">內容是執行緒的現用內容。</span><span class="sxs-lookup"><span data-stu-id="fdf44-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="fdf44-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="fdf44-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="fdf44-111">已從另一個框架回溯來計算內容。</span><span class="sxs-lookup"><span data-stu-id="fdf44-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf44-112">備註</span><span class="sxs-lookup"><span data-stu-id="fdf44-112">Remarks</span></span>  
 <span data-ttu-id="fdf44-113">`CorDebugSetContextFlag`提供[ICorDebugStackWalk：： SetCoNtext](icordebugstackwalk-setcontext-method.md)方法所使用的值。</span><span class="sxs-lookup"><span data-stu-id="fdf44-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdf44-114">需求</span><span class="sxs-lookup"><span data-stu-id="fdf44-114">Requirements</span></span>  
 <span data-ttu-id="fdf44-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdf44-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf44-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdf44-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdf44-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdf44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdf44-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf44-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf44-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="fdf44-119">See also</span></span>

- [<span data-ttu-id="fdf44-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="fdf44-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="fdf44-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="fdf44-121">Debugging</span></span>](index.md)
