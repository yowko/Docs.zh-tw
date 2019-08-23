---
title: ICorDebugDataTarget 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930827"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="8c072-102">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="8c072-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="8c072-103">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="8c072-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c072-104">方法</span><span class="sxs-lookup"><span data-stu-id="8c072-104">Methods</span></span>  
  
|<span data-ttu-id="8c072-105">方法</span><span class="sxs-lookup"><span data-stu-id="8c072-105">Method</span></span>|<span data-ttu-id="8c072-106">說明</span><span class="sxs-lookup"><span data-stu-id="8c072-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c072-107">GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="8c072-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="8c072-108">提供目標進程執行所在平臺的相關資訊, 包括處理器架構和作業系統。</span><span class="sxs-lookup"><span data-stu-id="8c072-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="8c072-109">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="8c072-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="8c072-110">從指定的位址開始, 取得連續記憶體的區塊, 並將它傳回給提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8c072-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="8c072-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="8c072-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="8c072-112">要求指定之執行緒的目前線程內容。</span><span class="sxs-lookup"><span data-stu-id="8c072-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c072-113">備註</span><span class="sxs-lookup"><span data-stu-id="8c072-113">Remarks</span></span>  
 <span data-ttu-id="8c072-114">`ICorDebugDataTarget`和其方法具有下列特性:</span><span class="sxs-lookup"><span data-stu-id="8c072-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="8c072-115">偵錯工具會呼叫這個介面上的方法, 以存取目標進程中的記憶體和其他資料。</span><span class="sxs-lookup"><span data-stu-id="8c072-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="8c072-116">偵錯工具用戶端必須將此介面實作為特定目標的適當 (例如, 即時進程或記憶體傾印)。</span><span class="sxs-lookup"><span data-stu-id="8c072-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="8c072-117">只能從在其他`ICorDebug*`介面中實作為方法來叫用方法。`ICorDebugDataTarget`</span><span class="sxs-lookup"><span data-stu-id="8c072-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="8c072-118">這可確保偵錯工具用戶端能夠控制要在哪一個執行緒上叫用它, 以及何時。</span><span class="sxs-lookup"><span data-stu-id="8c072-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="8c072-119">`ICorDebugDataTarget`執行必須一律傳回有關目標的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="8c072-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="8c072-120">在呼叫介面 ( `ICorDebug*` `ICorDebugDataTarget`也就是方法) 時, 目標進程應該會停止, 而且不會以任何方式變更。</span><span class="sxs-lookup"><span data-stu-id="8c072-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="8c072-121">如果目標是即時進程且其狀態變更, 必須再次呼叫[ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法, 以提供取代 ICorDebugProcess 實例。</span><span class="sxs-lookup"><span data-stu-id="8c072-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c072-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c072-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c072-123">需求</span><span class="sxs-lookup"><span data-stu-id="8c072-123">Requirements</span></span>  
 <span data-ttu-id="8c072-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c072-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c072-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c072-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c072-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c072-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c072-127">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c072-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c072-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c072-128">See also</span></span>

- [<span data-ttu-id="8c072-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8c072-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8c072-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="8c072-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
