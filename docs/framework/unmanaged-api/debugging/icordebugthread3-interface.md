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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378712"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="6ff9a-102">ICorDebugThread3 介面</span><span class="sxs-lookup"><span data-stu-id="6ff9a-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="6ff9a-103">提供[ICorDebugStackWalk](icordebugstackwalk-interface.md)和對應介面的進入點。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ff9a-104">方法</span><span class="sxs-lookup"><span data-stu-id="6ff9a-104">Methods</span></span>  
  
|<span data-ttu-id="6ff9a-105">方法</span><span class="sxs-lookup"><span data-stu-id="6ff9a-105">Method</span></span>|<span data-ttu-id="6ff9a-106">描述</span><span class="sxs-lookup"><span data-stu-id="6ff9a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ff9a-107">CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="6ff9a-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="6ff9a-108">為您要回溯其堆疊的執行緒建立[ICorDebugStackWalk](icordebugstackwalk-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="6ff9a-109">GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="6ff9a-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="6ff9a-110">傳回堆疊上的內部框架（[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)物件）陣列。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ff9a-111">備註</span><span class="sxs-lookup"><span data-stu-id="6ff9a-111">Remarks</span></span>  
 <span data-ttu-id="6ff9a-112">`ICorDebugThread3`是 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff9a-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ff9a-114">需求</span><span class="sxs-lookup"><span data-stu-id="6ff9a-114">Requirements</span></span>  
 <span data-ttu-id="6ff9a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff9a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ff9a-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ff9a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ff9a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ff9a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ff9a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ff9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff9a-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ff9a-119">See also</span></span>

- [<span data-ttu-id="6ff9a-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6ff9a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6ff9a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="6ff9a-121">Debugging</span></span>](index.md)
