---
title: ICorDebugChain Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32889a8e8867fc42b48413463095dda423f26b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409837"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="b7edb-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="b7edb-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="b7edb-103">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="b7edb-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7edb-104">方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-104">Methods</span></span>  
  
|<span data-ttu-id="b7edb-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-105">Method</span></span>|<span data-ttu-id="b7edb-106">描述</span><span class="sxs-lookup"><span data-stu-id="b7edb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7edb-107">EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="b7edb-108">取得列舉值，其中包含鏈結中的所有受管理的堆疊框架開頭為最新的框架。</span><span class="sxs-lookup"><span data-stu-id="b7edb-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="b7edb-109">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="b7edb-110">取得作用中 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="b7edb-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="b7edb-111">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="b7edb-112">取得由這個鏈結所呼叫。</span><span class="sxs-lookup"><span data-stu-id="b7edb-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="b7edb-113">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="b7edb-114">取得呼叫這個鏈結的鏈結。</span><span class="sxs-lookup"><span data-stu-id="b7edb-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="b7edb-115">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="b7edb-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="b7edb-116">Not implemented.</span></span>|  
|[<span data-ttu-id="b7edb-117">GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="b7edb-118">取得執行緒中的下一個框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="b7edb-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="b7edb-119">GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="b7edb-120">取得執行緒中先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="b7edb-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="b7edb-121">GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="b7edb-122">取得這個呼叫鏈結發生的原因。</span><span class="sxs-lookup"><span data-stu-id="b7edb-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="b7edb-123">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="b7edb-124">取得為這個鏈結的使用中部分設定的暫存器。</span><span class="sxs-lookup"><span data-stu-id="b7edb-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="b7edb-125">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="b7edb-126">取得這個鏈結的堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="b7edb-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="b7edb-127">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="b7edb-128">取得實體的執行緒，這個呼叫鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="b7edb-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="b7edb-129">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="b7edb-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="b7edb-130">取得值，指出這個鏈結是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b7edb-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7edb-131">備註</span><span class="sxs-lookup"><span data-stu-id="b7edb-131">Remarks</span></span>  
 <span data-ttu-id="b7edb-132">鏈結中的堆疊框架佔用連續的堆疊空間，而且共用相同的執行緒和內容。</span><span class="sxs-lookup"><span data-stu-id="b7edb-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="b7edb-133">鏈結可能代表其中一個 managed 或 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="b7edb-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="b7edb-134">空白`ICorDebugChain`的執行個體表示的 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="b7edb-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7edb-135">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b7edb-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7edb-136">需求</span><span class="sxs-lookup"><span data-stu-id="b7edb-136">Requirements</span></span>  
 <span data-ttu-id="b7edb-137">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7edb-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7edb-138">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7edb-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7edb-139">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7edb-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7edb-140">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7edb-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7edb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7edb-141">See Also</span></span>  
 [<span data-ttu-id="b7edb-142">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7edb-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
