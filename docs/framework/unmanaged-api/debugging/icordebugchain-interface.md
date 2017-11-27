---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f964b5390e601b518acad44dd6fd170399ff0af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="d2b0c-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="d2b0c-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="d2b0c-103">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2b0c-104">方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-104">Methods</span></span>  
  
|<span data-ttu-id="d2b0c-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-105">Method</span></span>|<span data-ttu-id="d2b0c-106">說明</span><span class="sxs-lookup"><span data-stu-id="d2b0c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2b0c-107">EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="d2b0c-108">取得列舉值，其中包含鏈結中的所有受管理的堆疊框架開頭為最新的框架。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="d2b0c-109">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="d2b0c-110">取得作用中 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="d2b0c-111">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="d2b0c-112">取得由這個鏈結所呼叫。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="d2b0c-113">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="d2b0c-114">取得呼叫這個鏈結的鏈結。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="d2b0c-115">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="d2b0c-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-116">Not implemented.</span></span>|  
|[<span data-ttu-id="d2b0c-117">GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="d2b0c-118">取得執行緒中的下一個框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="d2b0c-119">GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="d2b0c-120">取得執行緒中先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="d2b0c-121">GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="d2b0c-122">取得這個呼叫鏈結發生的原因。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="d2b0c-123">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="d2b0c-124">取得為這個鏈結的使用中部分設定的暫存器。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="d2b0c-125">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="d2b0c-126">取得這個鏈結的堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="d2b0c-127">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="d2b0c-128">取得實體的執行緒，這個呼叫鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="d2b0c-129">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="d2b0c-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="d2b0c-130">取得值，指出這個鏈結是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2b0c-131">備註</span><span class="sxs-lookup"><span data-stu-id="d2b0c-131">Remarks</span></span>  
 <span data-ttu-id="d2b0c-132">鏈結中的堆疊框架佔用連續的堆疊空間，而且共用相同的執行緒和內容。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="d2b0c-133">鏈結可能代表其中一個 managed 或 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="d2b0c-134">空白`ICorDebugChain`的執行個體表示的 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2b0c-135">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2b0c-136">需求</span><span class="sxs-lookup"><span data-stu-id="d2b0c-136">Requirements</span></span>  
 <span data-ttu-id="d2b0c-137">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2b0c-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2b0c-138">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2b0c-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2b0c-139">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2b0c-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2b0c-140">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2b0c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2b0c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2b0c-141">See Also</span></span>  
 [<span data-ttu-id="d2b0c-142">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d2b0c-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
