---
title: ICorDebugThread3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 015d0061e5be5bbc212243ca06f1d165abe4496a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729300"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="bd584-102">ICorDebugThread3 介面</span><span class="sxs-lookup"><span data-stu-id="bd584-102">ICorDebugThread3 Interface</span></span>

<span data-ttu-id="bd584-103">提供 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 和對應介面的進入點。</span><span class="sxs-lookup"><span data-stu-id="bd584-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd584-104">方法</span><span class="sxs-lookup"><span data-stu-id="bd584-104">Methods</span></span>  
  
|<span data-ttu-id="bd584-105">方法</span><span class="sxs-lookup"><span data-stu-id="bd584-105">Method</span></span>|<span data-ttu-id="bd584-106">描述</span><span class="sxs-lookup"><span data-stu-id="bd584-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd584-107">CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="bd584-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="bd584-108">為您想要回溯其堆疊的執行緒建立 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="bd584-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="bd584-109">GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="bd584-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="bd584-110">傳回內部框架的陣列， (堆疊上) 的 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="bd584-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd584-111">備註</span><span class="sxs-lookup"><span data-stu-id="bd584-111">Remarks</span></span>  

 <span data-ttu-id="bd584-112">`ICorDebugThread3` 是 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="bd584-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd584-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="bd584-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd584-114">需求</span><span class="sxs-lookup"><span data-stu-id="bd584-114">Requirements</span></span>  

 <span data-ttu-id="bd584-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd584-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd584-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd584-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd584-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd584-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd584-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd584-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd584-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd584-119">See also</span></span>

- [<span data-ttu-id="bd584-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bd584-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bd584-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="bd584-121">Debugging</span></span>](index.md)
