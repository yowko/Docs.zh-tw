---
title: ICorDebugChain 介面
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: a0285970a8a42c078aa663579e1d5998d0d1c037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724451"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="80ce7-102">ICorDebugChain 介面</span><span class="sxs-lookup"><span data-stu-id="80ce7-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="80ce7-103">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="80ce7-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80ce7-104">方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-104">Methods</span></span>  
  
|<span data-ttu-id="80ce7-105">方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-105">Method</span></span>|<span data-ttu-id="80ce7-106">描述</span><span class="sxs-lookup"><span data-stu-id="80ce7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80ce7-107">EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="80ce7-108">取得枚舉器，其中包含鏈中的所有 managed 堆疊框架（從最新的框架開始）。</span><span class="sxs-lookup"><span data-stu-id="80ce7-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="80ce7-109">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="80ce7-110">取得使用中的 (，也就是鏈上最新的) 框架。</span><span class="sxs-lookup"><span data-stu-id="80ce7-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="80ce7-111">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="80ce7-112">取得此鏈所呼叫的鏈。</span><span class="sxs-lookup"><span data-stu-id="80ce7-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="80ce7-113">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="80ce7-114">取得呼叫此鏈的鏈。</span><span class="sxs-lookup"><span data-stu-id="80ce7-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="80ce7-115">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="80ce7-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="80ce7-116">Not implemented.</span></span>|  
|[<span data-ttu-id="80ce7-117">GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="80ce7-118">取得執行緒的下一鏈框架。</span><span class="sxs-lookup"><span data-stu-id="80ce7-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="80ce7-119">GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="80ce7-120">取得執行緒的上一鏈框架。</span><span class="sxs-lookup"><span data-stu-id="80ce7-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="80ce7-121">GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="80ce7-122">取得此呼叫鏈創世的原因。</span><span class="sxs-lookup"><span data-stu-id="80ce7-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="80ce7-123">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="80ce7-124">取得此鏈之使用中部分的註冊集。</span><span class="sxs-lookup"><span data-stu-id="80ce7-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="80ce7-125">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="80ce7-126">取得此鏈之堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="80ce7-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="80ce7-127">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="80ce7-128">取得此呼叫鏈所屬的實體執行緒。</span><span class="sxs-lookup"><span data-stu-id="80ce7-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="80ce7-129">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="80ce7-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="80ce7-130">取得值，這個值表示此鏈是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="80ce7-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ce7-131">備註</span><span class="sxs-lookup"><span data-stu-id="80ce7-131">Remarks</span></span>  

 <span data-ttu-id="80ce7-132">鏈中的堆疊框架會佔用連續的堆疊空間，並共用相同的執行緒和內容。</span><span class="sxs-lookup"><span data-stu-id="80ce7-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="80ce7-133">連鎖可能代表受控或非受控碼鏈。</span><span class="sxs-lookup"><span data-stu-id="80ce7-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="80ce7-134">空的 `ICorDebugChain` 實例代表非受控碼鏈。</span><span class="sxs-lookup"><span data-stu-id="80ce7-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80ce7-135">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="80ce7-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ce7-136">需求</span><span class="sxs-lookup"><span data-stu-id="80ce7-136">Requirements</span></span>  

 <span data-ttu-id="80ce7-137">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80ce7-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ce7-138">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80ce7-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80ce7-139">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80ce7-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ce7-140">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ce7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ce7-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80ce7-141">See also</span></span>

- [<span data-ttu-id="80ce7-142">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="80ce7-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
