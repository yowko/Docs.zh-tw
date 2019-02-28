---
title: ICorDebugHandleValue 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dddc1665dff5c1a0629d25aa99066ce6eeca94a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981435"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="b1ded-102">ICorDebugHandleValue 介面</span><span class="sxs-lookup"><span data-stu-id="b1ded-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="b1ded-103">ICorDebugReferenceValue，代表要偵錯工具已建立為記憶體回收控制代碼的參考值的子類別。</span><span class="sxs-lookup"><span data-stu-id="b1ded-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1ded-104">方法</span><span class="sxs-lookup"><span data-stu-id="b1ded-104">Methods</span></span>  
  
|<span data-ttu-id="b1ded-105">方法</span><span class="sxs-lookup"><span data-stu-id="b1ded-105">Method</span></span>|<span data-ttu-id="b1ded-106">描述</span><span class="sxs-lookup"><span data-stu-id="b1ded-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1ded-107">Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="b1ded-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="b1ded-108">釋放控制代碼所參考`ICorDebugHandleValue`未明確地釋放介面指標的物件。</span><span class="sxs-lookup"><span data-stu-id="b1ded-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="b1ded-109">GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="b1ded-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="b1ded-110">取得描述的控制代碼所參考類型的 CorDebugHandleType 值`ICorDebugHandleValue`。</span><span class="sxs-lookup"><span data-stu-id="b1ded-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ded-111">備註</span><span class="sxs-lookup"><span data-stu-id="b1ded-111">Remarks</span></span>  
 <span data-ttu-id="b1ded-112">`ICorDebugReferenceValue`物件都無效的執行中的偵錯的程式碼中斷。</span><span class="sxs-lookup"><span data-stu-id="b1ded-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="b1ded-113">`ICorDebugHandleValue`維護透過符號和接續，其參考，直到明確釋放為止。</span><span class="sxs-lookup"><span data-stu-id="b1ded-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1ded-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b1ded-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ded-115">需求</span><span class="sxs-lookup"><span data-stu-id="b1ded-115">Requirements</span></span>  
 <span data-ttu-id="b1ded-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1ded-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ded-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1ded-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1ded-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1ded-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ded-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ded-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ded-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ded-120">See also</span></span>
- [<span data-ttu-id="b1ded-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b1ded-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
