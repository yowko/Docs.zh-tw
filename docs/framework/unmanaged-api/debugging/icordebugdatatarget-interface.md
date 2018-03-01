---
title: "ICorDebugDataTarget 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="e5383-102">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="e5383-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="e5383-103">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="e5383-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5383-104">方法</span><span class="sxs-lookup"><span data-stu-id="e5383-104">Methods</span></span>  
  
|<span data-ttu-id="e5383-105">方法</span><span class="sxs-lookup"><span data-stu-id="e5383-105">Method</span></span>|<span data-ttu-id="e5383-106">描述</span><span class="sxs-lookup"><span data-stu-id="e5383-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5383-107">GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="e5383-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="e5383-108">提供的平台，包括處理器架構與目標處理序執行所在的作業系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e5383-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="e5383-109">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="e5383-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="e5383-110">取得指定的位址，開頭的連續記憶體區塊，並傳回在提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e5383-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="e5383-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="e5383-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="e5383-112">要求指定的執行緒目前的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="e5383-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5383-113">備註</span><span class="sxs-lookup"><span data-stu-id="e5383-113">Remarks</span></span>  
 <span data-ttu-id="e5383-114">`ICorDebugDataTarget`其方法具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="e5383-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="e5383-115">偵錯服務會呼叫這個介面來存取記憶體和目標處理序中的其他資料上的方法。</span><span class="sxs-lookup"><span data-stu-id="e5383-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="e5383-116">偵錯工具用戶端必須實作此介面適用於特定的目標 （例如，即時處理序或記憶體傾印）。</span><span class="sxs-lookup"><span data-stu-id="e5383-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="e5383-117">`ICorDebugDataTarget`可以叫用方法只會從其他實作之方法內`ICorDebug*`介面。</span><span class="sxs-lookup"><span data-stu-id="e5383-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="e5383-118">這可確保具有控制哪一個執行緒上叫用它，而當偵錯工具用戶端。</span><span class="sxs-lookup"><span data-stu-id="e5383-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="e5383-119">`ICorDebugDataTarget`實作必須一律會傳回目標的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="e5383-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="e5383-120">目標處理序應該停止，並不會變更時的任何方式`ICorDebug*`介面 (因此`ICorDebugDataTarget`方法) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5383-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="e5383-121">如果目標是即時處理序和其狀態變更， [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法必須再次呼叫，以提供取代 ICorDebugProcess 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5383-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5383-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5383-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5383-123">需求</span><span class="sxs-lookup"><span data-stu-id="e5383-123">Requirements</span></span>  
 <span data-ttu-id="e5383-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5383-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5383-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5383-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5383-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5383-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5383-127">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5383-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5383-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5383-128">See Also</span></span>  
 [<span data-ttu-id="e5383-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e5383-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e5383-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="e5383-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
