---
title: ICorDebugStackWalk 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378911"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="555e2-102">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="555e2-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="555e2-103">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="555e2-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="555e2-104">方法</span><span class="sxs-lookup"><span data-stu-id="555e2-104">Methods</span></span>  
  
|<span data-ttu-id="555e2-105">方法</span><span class="sxs-lookup"><span data-stu-id="555e2-105">Method</span></span>|<span data-ttu-id="555e2-106">描述</span><span class="sxs-lookup"><span data-stu-id="555e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="555e2-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="555e2-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="555e2-108">傳回物件中目前框架的內容 `ICorDebugStackWalk` 。</span><span class="sxs-lookup"><span data-stu-id="555e2-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="555e2-109">SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="555e2-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="555e2-110">將 `ICorDebugStackWalk` 物件的目前內容設定為執行緒的有效內容。</span><span class="sxs-lookup"><span data-stu-id="555e2-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="555e2-111">下一個方法</span><span class="sxs-lookup"><span data-stu-id="555e2-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="555e2-112">將 `ICorDebugStackWalk` 物件移到下一個框架。</span><span class="sxs-lookup"><span data-stu-id="555e2-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="555e2-113">GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="555e2-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="555e2-114">取得物件中的目前框架 `ICorDebugStackWalk` 。</span><span class="sxs-lookup"><span data-stu-id="555e2-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="555e2-115">備註</span><span class="sxs-lookup"><span data-stu-id="555e2-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="555e2-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="555e2-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="555e2-117">需求</span><span class="sxs-lookup"><span data-stu-id="555e2-117">Requirements</span></span>  
 <span data-ttu-id="555e2-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="555e2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="555e2-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="555e2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="555e2-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="555e2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="555e2-121">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="555e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555e2-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="555e2-122">See also</span></span>

- [<span data-ttu-id="555e2-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="555e2-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="555e2-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="555e2-124">Debugging</span></span>](index.md)
