---
title: ICorDebugHandleValue Interface
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
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138473"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="d9631-102">ICorDebugHandleValue Interface</span><span class="sxs-lookup"><span data-stu-id="d9631-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="d9631-103">ICorDebugReferenceValue 的子類別，代表偵錯工具已為其建立垃圾收集控制碼的參考值。</span><span class="sxs-lookup"><span data-stu-id="d9631-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9631-104">方法</span><span class="sxs-lookup"><span data-stu-id="d9631-104">Methods</span></span>  
  
|<span data-ttu-id="d9631-105">方法</span><span class="sxs-lookup"><span data-stu-id="d9631-105">Method</span></span>|<span data-ttu-id="d9631-106">描述</span><span class="sxs-lookup"><span data-stu-id="d9631-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9631-107">Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="d9631-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="d9631-108">釋放這個 `ICorDebugHandleValue` 物件所參考的控制碼，而不明確釋放介面指標。</span><span class="sxs-lookup"><span data-stu-id="d9631-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="d9631-109">GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="d9631-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="d9631-110">取得描述此 `ICorDebugHandleValue`所參考之控制碼種類的 CorDebugHandleType 值。</span><span class="sxs-lookup"><span data-stu-id="d9631-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9631-111">備註</span><span class="sxs-lookup"><span data-stu-id="d9631-111">Remarks</span></span>  
 <span data-ttu-id="d9631-112">在執行已調試的程式碼時，`ICorDebugReferenceValue` 物件會使其失效。</span><span class="sxs-lookup"><span data-stu-id="d9631-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="d9631-113">`ICorDebugHandleValue` 會透過中斷和接續來維護其參考，直到明確釋放為止。</span><span class="sxs-lookup"><span data-stu-id="d9631-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9631-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d9631-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9631-115">需求</span><span class="sxs-lookup"><span data-stu-id="d9631-115">Requirements</span></span>  
 <span data-ttu-id="d9631-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9631-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9631-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9631-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9631-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9631-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9631-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9631-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9631-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d9631-120">See also</span></span>

- [<span data-ttu-id="d9631-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d9631-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
