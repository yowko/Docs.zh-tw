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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 612e0f84302d5bee6479264ef2dbba4c7152657e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422542"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="6416d-102">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="6416d-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="6416d-103">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="6416d-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6416d-104">方法</span><span class="sxs-lookup"><span data-stu-id="6416d-104">Methods</span></span>  
  
|<span data-ttu-id="6416d-105">方法</span><span class="sxs-lookup"><span data-stu-id="6416d-105">Method</span></span>|<span data-ttu-id="6416d-106">描述</span><span class="sxs-lookup"><span data-stu-id="6416d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6416d-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="6416d-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="6416d-108">傳回目前的框架中的內容`ICorDebugStackWalk`物件。</span><span class="sxs-lookup"><span data-stu-id="6416d-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="6416d-109">SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="6416d-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="6416d-110">設定`ICorDebugStackWalk`物件的目前有效的內容執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="6416d-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="6416d-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="6416d-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="6416d-112">移動`ICorDebugStackWalk`下一個畫面格的物件。</span><span class="sxs-lookup"><span data-stu-id="6416d-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="6416d-113">GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="6416d-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="6416d-114">取得目前的框架中`ICorDebugStackWalk`物件。</span><span class="sxs-lookup"><span data-stu-id="6416d-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6416d-115">備註</span><span class="sxs-lookup"><span data-stu-id="6416d-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6416d-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6416d-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6416d-117">需求</span><span class="sxs-lookup"><span data-stu-id="6416d-117">Requirements</span></span>  
 <span data-ttu-id="6416d-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6416d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6416d-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6416d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6416d-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6416d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6416d-121">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6416d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6416d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6416d-122">See Also</span></span>  
 [<span data-ttu-id="6416d-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6416d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6416d-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="6416d-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
