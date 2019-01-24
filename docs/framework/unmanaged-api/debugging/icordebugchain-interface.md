---
title: ICorDebugChain 介面 1
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
ms.openlocfilehash: e0bb716f1ad4087642a76dc84266ec6d3f46c1ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571200"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="4c832-102">ICorDebugChain 介面 1</span><span class="sxs-lookup"><span data-stu-id="4c832-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="4c832-103">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="4c832-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c832-104">方法</span><span class="sxs-lookup"><span data-stu-id="4c832-104">Methods</span></span>  
  
|<span data-ttu-id="4c832-105">方法</span><span class="sxs-lookup"><span data-stu-id="4c832-105">Method</span></span>|<span data-ttu-id="4c832-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c832-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c832-107">EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="4c832-108">取得列舉值，其中包含所有的受管理的堆疊框架，在鏈結中，從最新的框架開始。</span><span class="sxs-lookup"><span data-stu-id="4c832-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="4c832-109">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="4c832-110">取得使用 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="4c832-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="4c832-111">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="4c832-112">取得這個鏈結所呼叫函式鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="4c832-113">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="4c832-114">取得呼叫這個接收鏈結的鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="4c832-115">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="4c832-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="4c832-116">Not implemented.</span></span>|  
|[<span data-ttu-id="4c832-117">GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="4c832-118">取得執行緒中的下一個框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="4c832-119">GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="4c832-120">取得執行緒先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="4c832-121">GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="4c832-122">取得這個呼叫鏈結發生的原因。</span><span class="sxs-lookup"><span data-stu-id="4c832-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="4c832-123">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="4c832-124">取得設定此鏈結的使用中部分的暫存器。</span><span class="sxs-lookup"><span data-stu-id="4c832-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="4c832-125">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="4c832-126">取得這個鏈結的堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="4c832-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="4c832-127">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="4c832-128">取得實體的執行緒，此呼叫鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="4c832-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="4c832-129">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="4c832-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="4c832-130">取得值，指出這個鏈結是否正在執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c832-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c832-131">備註</span><span class="sxs-lookup"><span data-stu-id="4c832-131">Remarks</span></span>  
 <span data-ttu-id="4c832-132">鏈結中的堆疊框架會佔據連續的堆疊空間，並共用相同的執行緒和內容。</span><span class="sxs-lookup"><span data-stu-id="4c832-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="4c832-133">鏈結可能代表其中一個 managed 或 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="4c832-134">空白`ICorDebugChain`執行個體代表 unmanaged 程式碼鏈結。</span><span class="sxs-lookup"><span data-stu-id="4c832-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c832-135">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c832-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c832-136">需求</span><span class="sxs-lookup"><span data-stu-id="4c832-136">Requirements</span></span>  
 <span data-ttu-id="4c832-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c832-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c832-138">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c832-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c832-139">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c832-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c832-140">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c832-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c832-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c832-141">See also</span></span>
- [<span data-ttu-id="4c832-142">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4c832-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
