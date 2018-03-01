---
title: ICorDebugHandleValue Interface1
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
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="55fee-102">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="55fee-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="55fee-103">ICorDebugReferenceValue，表示要偵錯工具已建立的記憶體回收控制代碼的參考值的子類別。</span><span class="sxs-lookup"><span data-stu-id="55fee-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55fee-104">方法</span><span class="sxs-lookup"><span data-stu-id="55fee-104">Methods</span></span>  
  
|<span data-ttu-id="55fee-105">方法</span><span class="sxs-lookup"><span data-stu-id="55fee-105">Method</span></span>|<span data-ttu-id="55fee-106">描述</span><span class="sxs-lookup"><span data-stu-id="55fee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55fee-107">Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="55fee-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="55fee-108">釋放的控制代碼所參考`ICorDebugHandleValue`物件，而不會明確地釋放的介面指標。</span><span class="sxs-lookup"><span data-stu-id="55fee-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="55fee-109">GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="55fee-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="55fee-110">取得描述類型的控制代碼所參考的 CorDebugHandleType 值`ICorDebugHandleValue`。</span><span class="sxs-lookup"><span data-stu-id="55fee-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55fee-111">備註</span><span class="sxs-lookup"><span data-stu-id="55fee-111">Remarks</span></span>  
 <span data-ttu-id="55fee-112">`ICorDebugReferenceValue`物件無效的執行中的偵錯的程式碼中斷。</span><span class="sxs-lookup"><span data-stu-id="55fee-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="55fee-113">`ICorDebugHandleValue`維護符號和接續，透過其參考，直到明確釋放為止。</span><span class="sxs-lookup"><span data-stu-id="55fee-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55fee-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="55fee-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55fee-115">需求</span><span class="sxs-lookup"><span data-stu-id="55fee-115">Requirements</span></span>  
 <span data-ttu-id="55fee-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55fee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55fee-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55fee-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55fee-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55fee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55fee-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55fee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fee-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="55fee-120">See Also</span></span>  
 [<span data-ttu-id="55fee-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="55fee-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
