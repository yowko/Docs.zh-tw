---
title: ICorDebugRuntimeUnwindableFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f006085aba140264e2a2605adce39924dbe082e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568110"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="bbf3d-102">ICorDebugRuntimeUnwindableFrame 介面</span><span class="sxs-lookup"><span data-stu-id="bbf3d-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="bbf3d-103">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbf3d-104">備註</span><span class="sxs-lookup"><span data-stu-id="bbf3d-104">Remarks</span></span>  
 <span data-ttu-id="bbf3d-105">`ICorDebugRuntimeUnwindableFrame` 是 ICorDebugFrame 介面的特製化的版本。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="bbf3d-106">它會使用需要回溯上目前的堆疊框架執行階段的 unmanaged 方法。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="bbf3d-107">現有的回溯慣例無法運作，因為它們不會使用 JIT 編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="bbf3d-108">當偵錯工具會看到無法還原的畫面格時，應使用[icordebugstackwalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)回溯，但是它的方法應該會執行檢查本身。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="bbf3d-109">當偵錯工具收到`ICorDebugRuntimeUnwindableFrame`，它可以呼叫[icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法來擷取框架的內容。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf3d-110">需求</span><span class="sxs-lookup"><span data-stu-id="bbf3d-110">Requirements</span></span>  
 <span data-ttu-id="bbf3d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bbf3d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf3d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbf3d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbf3d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbf3d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbf3d-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf3d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf3d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf3d-115">See also</span></span>
- [<span data-ttu-id="bbf3d-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bbf3d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bbf3d-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="bbf3d-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
