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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d34a3395605505ca0ebda072e33d8083d51123a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185870"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="2f758-102">ICorDebugThread3 介面</span><span class="sxs-lookup"><span data-stu-id="2f758-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="2f758-103">提供的進入點[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)和對應的介面。</span><span class="sxs-lookup"><span data-stu-id="2f758-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f758-104">方法</span><span class="sxs-lookup"><span data-stu-id="2f758-104">Methods</span></span>  
  
|<span data-ttu-id="2f758-105">方法</span><span class="sxs-lookup"><span data-stu-id="2f758-105">Method</span></span>|<span data-ttu-id="2f758-106">描述</span><span class="sxs-lookup"><span data-stu-id="2f758-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f758-107">CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="2f758-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="2f758-108">會建立[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒要回溯的堆疊的物件。</span><span class="sxs-lookup"><span data-stu-id="2f758-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="2f758-109">GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="2f758-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="2f758-110">傳回陣列的內部框架 ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件) 在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="2f758-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f758-111">備註</span><span class="sxs-lookup"><span data-stu-id="2f758-111">Remarks</span></span>  
 <span data-ttu-id="2f758-112">`ICorDebugThread3` 是 ICorDebugThread 介面的邏輯擴充功能。</span><span class="sxs-lookup"><span data-stu-id="2f758-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f758-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2f758-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f758-114">需求</span><span class="sxs-lookup"><span data-stu-id="2f758-114">Requirements</span></span>  
 <span data-ttu-id="2f758-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f758-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f758-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f758-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f758-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f758-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f758-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f758-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f758-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f758-119">See also</span></span>

- [<span data-ttu-id="2f758-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2f758-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2f758-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="2f758-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
