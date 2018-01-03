---
title: "ICorDebugThread3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cfb3267637210567f3df9fa08bb75135dc585ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="eecc9-102">ICorDebugThread3 介面</span><span class="sxs-lookup"><span data-stu-id="eecc9-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="eecc9-103">提供的進入點[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)及對應介面。</span><span class="sxs-lookup"><span data-stu-id="eecc9-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eecc9-104">方法</span><span class="sxs-lookup"><span data-stu-id="eecc9-104">Methods</span></span>  
  
|<span data-ttu-id="eecc9-105">方法</span><span class="sxs-lookup"><span data-stu-id="eecc9-105">Method</span></span>|<span data-ttu-id="eecc9-106">描述</span><span class="sxs-lookup"><span data-stu-id="eecc9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eecc9-107">CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="eecc9-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="eecc9-108">建立[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒的堆疊回溯您想要的物件。</span><span class="sxs-lookup"><span data-stu-id="eecc9-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="eecc9-109">GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="eecc9-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="eecc9-110">傳回內部框架的陣列 ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件) 堆疊上。</span><span class="sxs-lookup"><span data-stu-id="eecc9-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eecc9-111">備註</span><span class="sxs-lookup"><span data-stu-id="eecc9-111">Remarks</span></span>  
 <span data-ttu-id="eecc9-112">`ICorDebugThread3`是 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="eecc9-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eecc9-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eecc9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eecc9-114">需求</span><span class="sxs-lookup"><span data-stu-id="eecc9-114">Requirements</span></span>  
 <span data-ttu-id="eecc9-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eecc9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eecc9-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eecc9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eecc9-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eecc9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eecc9-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eecc9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eecc9-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="eecc9-119">See Also</span></span>  
 [<span data-ttu-id="eecc9-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eecc9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="eecc9-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="eecc9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
