---
title: ICorDebugMutableDataTarget 介面
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419526"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="bd4f1-102">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="bd4f1-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="bd4f1-103">擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以支援可變動的資料目標。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd4f1-104">方法</span><span class="sxs-lookup"><span data-stu-id="bd4f1-104">Methods</span></span>  
  
|<span data-ttu-id="bd4f1-105">方法</span><span class="sxs-lookup"><span data-stu-id="bd4f1-105">Method</span></span>|<span data-ttu-id="bd4f1-106">描述</span><span class="sxs-lookup"><span data-stu-id="bd4f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd4f1-107">ContinueStatusChanged 方法</span><span class="sxs-lookup"><span data-stu-id="bd4f1-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="bd4f1-108">變更指定執行緒上未處理之偵錯事件的接續狀態。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="bd4f1-109">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="bd4f1-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="bd4f1-110">設定執行緒的內容 (登錄值)。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="bd4f1-111">WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="bd4f1-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="bd4f1-112">將記憶體寫入目標處理序位址空間。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd4f1-113">備註</span><span class="sxs-lookup"><span data-stu-id="bd4f1-113">Remarks</span></span>  
 <span data-ttu-id="bd4f1-114">這個延伸模組[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面可以實作的偵錯工具想要修改目標處理序 （例如，若要執行即時入侵式偵錯）。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="bd4f1-115">上述所有方法都是選擇性的，未實作這個介面或無法呼叫這些方法，並不會失去以核心檢查為基礎的偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="bd4f1-116">這些方法中的任何失敗 `HRESULT` 都會以 `HRESULT` 形式從 ICorDebug 方法呼叫向外傳播。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="bd4f1-117">請注意，單一 ICorDebug 方法呼叫可能會導致多項變動，沒有任何機制可確保相關的變動會以交易方式 (全有或全無) 來套用。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="bd4f1-118">這表示如果某項變動在其他變動成功之後失敗 (在相同的 ICorDebug 呼叫中)，目標處理序的狀態可能會不一致，因此偵錯可能會變成不可靠。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd4f1-119">需求</span><span class="sxs-lookup"><span data-stu-id="bd4f1-119">Requirements</span></span>  
 <span data-ttu-id="bd4f1-120">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd4f1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd4f1-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd4f1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd4f1-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd4f1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd4f1-123">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd4f1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd4f1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd4f1-124">See Also</span></span>  
 [<span data-ttu-id="bd4f1-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bd4f1-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bd4f1-126">偵錯</span><span class="sxs-lookup"><span data-stu-id="bd4f1-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
