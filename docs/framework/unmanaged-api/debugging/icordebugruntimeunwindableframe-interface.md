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
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379391"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="aa38f-102">ICorDebugRuntimeUnwindableFrame 介面</span><span class="sxs-lookup"><span data-stu-id="aa38f-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="aa38f-103">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="aa38f-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa38f-104">備註</span><span class="sxs-lookup"><span data-stu-id="aa38f-104">Remarks</span></span>  
 <span data-ttu-id="aa38f-105">`ICorDebugRuntimeUnwindableFrame`是 ICorDebugFrame 介面的特殊化版本。</span><span class="sxs-lookup"><span data-stu-id="aa38f-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="aa38f-106">這是由需要執行時間在目前堆疊上回溯框架的非受控方法所使用。</span><span class="sxs-lookup"><span data-stu-id="aa38f-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="aa38f-107">現有的回溯慣例無法正常執行，因為它們不會使用 JIT 編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa38f-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="aa38f-108">當偵錯工具看到 unwindable 框架時，應該使用[ICorDebugStackWalk：： Next](icordebugstackwalk-next-method.md)方法來回溯它，但它應該執行檢查本身。</span><span class="sxs-lookup"><span data-stu-id="aa38f-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="aa38f-109">當偵錯工具接收到時 `ICorDebugRuntimeUnwindableFrame` ，它可以呼叫[ICorDebugStackWalk：： GetCoNtext](icordebugstackwalk-getcontext-method.md)方法來抓取框架的內容。</span><span class="sxs-lookup"><span data-stu-id="aa38f-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa38f-110">需求</span><span class="sxs-lookup"><span data-stu-id="aa38f-110">Requirements</span></span>  
 <span data-ttu-id="aa38f-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa38f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa38f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa38f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa38f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa38f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa38f-114">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa38f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa38f-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa38f-115">See also</span></span>

- [<span data-ttu-id="aa38f-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aa38f-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="aa38f-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="aa38f-117">Debugging</span></span>](index.md)
