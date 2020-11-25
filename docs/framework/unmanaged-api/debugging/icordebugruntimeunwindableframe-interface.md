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
ms.openlocfilehash: 6619b8888588341f23a93b83865cd2e75cc9b3db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712010"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="58ef1-102">ICorDebugRuntimeUnwindableFrame 介面</span><span class="sxs-lookup"><span data-stu-id="58ef1-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>

<span data-ttu-id="58ef1-103">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="58ef1-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ef1-104">備註</span><span class="sxs-lookup"><span data-stu-id="58ef1-104">Remarks</span></span>  

 <span data-ttu-id="58ef1-105">`ICorDebugRuntimeUnwindableFrame` 是 ICorDebugFrame 介面的特製化版本。</span><span class="sxs-lookup"><span data-stu-id="58ef1-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="58ef1-106">它是由要求執行時間在目前堆疊上回溯框架的非受控方法所使用。</span><span class="sxs-lookup"><span data-stu-id="58ef1-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="58ef1-107">現有的回溯慣例無法運作，因為它們不會使用 JIT 編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="58ef1-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="58ef1-108">當偵錯工具看到 unwindable 框架時，它應該使用 [ICorDebugStackWalk：： Next](icordebugstackwalk-next-method.md) 方法來將它回溯，但它應該會執行檢查。</span><span class="sxs-lookup"><span data-stu-id="58ef1-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="58ef1-109">當偵錯工具收到時 `ICorDebugRuntimeUnwindableFrame` ，它可以呼叫 [ICorDebugStackWalk：： GetCoNtext](icordebugstackwalk-getcontext-method.md) 方法來取出框架的內容。</span><span class="sxs-lookup"><span data-stu-id="58ef1-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ef1-110">需求</span><span class="sxs-lookup"><span data-stu-id="58ef1-110">Requirements</span></span>  

 <span data-ttu-id="58ef1-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58ef1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ef1-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ef1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ef1-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ef1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ef1-114">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ef1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ef1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ef1-115">See also</span></span>

- [<span data-ttu-id="58ef1-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58ef1-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="58ef1-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="58ef1-117">Debugging</span></span>](index.md)
