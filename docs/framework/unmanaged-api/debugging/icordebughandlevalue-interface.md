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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915012"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="1b7ce-102">ICorDebugHandleValue Interface</span><span class="sxs-lookup"><span data-stu-id="1b7ce-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="1b7ce-103">ICorDebugReferenceValue 的子類別, 代表偵錯工具已為其建立垃圾收集控制碼的參考值。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b7ce-104">方法</span><span class="sxs-lookup"><span data-stu-id="1b7ce-104">Methods</span></span>  
  
|<span data-ttu-id="1b7ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="1b7ce-105">Method</span></span>|<span data-ttu-id="1b7ce-106">描述</span><span class="sxs-lookup"><span data-stu-id="1b7ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b7ce-107">Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="1b7ce-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="1b7ce-108">釋放這個`ICorDebugHandleValue`物件所參考的控制碼, 而不明確釋放介面指標。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="1b7ce-109">GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="1b7ce-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="1b7ce-110">取得 CorDebugHandleType 值, 描述這個`ICorDebugHandleValue`所參考的控制碼種類。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b7ce-111">備註</span><span class="sxs-lookup"><span data-stu-id="1b7ce-111">Remarks</span></span>  
 <span data-ttu-id="1b7ce-112">在`ICorDebugReferenceValue`執行已調試的程式碼時, 物件會因為中斷而失效。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="1b7ce-113">會透過中斷和接續來維護其參考,直到明確釋放為止。`ICorDebugHandleValue`</span><span class="sxs-lookup"><span data-stu-id="1b7ce-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b7ce-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b7ce-115">需求</span><span class="sxs-lookup"><span data-stu-id="1b7ce-115">Requirements</span></span>  
 <span data-ttu-id="1b7ce-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b7ce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b7ce-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b7ce-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b7ce-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b7ce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b7ce-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b7ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7ce-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b7ce-120">See also</span></span>

- [<span data-ttu-id="1b7ce-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1b7ce-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
