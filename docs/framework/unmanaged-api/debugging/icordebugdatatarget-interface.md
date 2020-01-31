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
ms.openlocfilehash: 9029d53872108bc1953fd22c584b6e01a6f3c7ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788861"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="2439a-102">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="2439a-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="2439a-103">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="2439a-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2439a-104">方法</span><span class="sxs-lookup"><span data-stu-id="2439a-104">Methods</span></span>  
  
|<span data-ttu-id="2439a-105">方法</span><span class="sxs-lookup"><span data-stu-id="2439a-105">Method</span></span>|<span data-ttu-id="2439a-106">描述</span><span class="sxs-lookup"><span data-stu-id="2439a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2439a-107">GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="2439a-107">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="2439a-108">提供目標進程執行所在平臺的相關資訊，包括處理器架構和作業系統。</span><span class="sxs-lookup"><span data-stu-id="2439a-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="2439a-109">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="2439a-109">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="2439a-110">從指定的位址開始，取得連續記憶體的區塊，並將它傳回給提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2439a-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="2439a-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="2439a-111">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="2439a-112">要求指定之執行緒的目前線程內容。</span><span class="sxs-lookup"><span data-stu-id="2439a-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2439a-113">備註</span><span class="sxs-lookup"><span data-stu-id="2439a-113">Remarks</span></span>  
 <span data-ttu-id="2439a-114">`ICorDebugDataTarget` 和其方法具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="2439a-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="2439a-115">偵錯工具會呼叫這個介面上的方法，以存取目標進程中的記憶體和其他資料。</span><span class="sxs-lookup"><span data-stu-id="2439a-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="2439a-116">偵錯工具用戶端必須將此介面實作為特定目標的適當（例如，即時進程或記憶體傾印）。</span><span class="sxs-lookup"><span data-stu-id="2439a-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="2439a-117">只能從在其他 `ICorDebug*` 介面中執行的方法內叫用 `ICorDebugDataTarget` 方法。</span><span class="sxs-lookup"><span data-stu-id="2439a-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="2439a-118">這可確保偵錯工具用戶端能夠控制要在哪一個執行緒上叫用它，以及何時。</span><span class="sxs-lookup"><span data-stu-id="2439a-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="2439a-119">`ICorDebugDataTarget` 的執行必須一律傳回有關目標的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="2439a-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="2439a-120">在呼叫 `ICorDebug*` 介面（因此 `ICorDebugDataTarget` 方法）時，目標進程應該停止且不會變更。</span><span class="sxs-lookup"><span data-stu-id="2439a-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="2439a-121">如果目標是即時進程且其狀態變更，必須再次呼叫[ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)方法，以提供取代 ICorDebugProcess 實例。</span><span class="sxs-lookup"><span data-stu-id="2439a-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2439a-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2439a-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2439a-123">需求</span><span class="sxs-lookup"><span data-stu-id="2439a-123">Requirements</span></span>  
 <span data-ttu-id="2439a-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2439a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2439a-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2439a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2439a-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2439a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2439a-127">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2439a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2439a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="2439a-128">See also</span></span>

- [<span data-ttu-id="2439a-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2439a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2439a-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="2439a-130">Debugging</span></span>](index.md)
