---
title: "ICorDebugExceptionDebugEvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97bbd9374b8a3f938f42b8ddd001049a2e7a324c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="7b7b4-102">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7b7b4-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="7b7b4-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b7b4-104">方法</span><span class="sxs-lookup"><span data-stu-id="7b7b4-104">Methods</span></span>  
  
|<span data-ttu-id="7b7b4-105">方法</span><span class="sxs-lookup"><span data-stu-id="7b7b4-105">Method</span></span>|<span data-ttu-id="7b7b4-106">描述</span><span class="sxs-lookup"><span data-stu-id="7b7b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b7b4-107">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="7b7b4-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="7b7b4-108">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="7b7b4-109">GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="7b7b4-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="7b7b4-110">取得這個例外狀況偵錯事件的原生介面指標。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="7b7b4-111">GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="7b7b4-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="7b7b4-112">取得這個例外狀況偵錯事件的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b7b4-113">備註</span><span class="sxs-lookup"><span data-stu-id="7b7b4-113">Remarks</span></span>  
 <span data-ttu-id="7b7b4-114">`ICorDebugExceptionDebugEvent` 介面由下列事件類型實作：</span><span class="sxs-lookup"><span data-stu-id="7b7b4-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="7b7b4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7b7b4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7b7b4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7b7b4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7b7b4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="7b7b4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7b7b4-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="7b7b4-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="7b7b4-119">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="7b7b4-120">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7b4-121">需求</span><span class="sxs-lookup"><span data-stu-id="7b7b4-121">Requirements</span></span>  
 <span data-ttu-id="7b7b4-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b7b4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7b4-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b7b4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b7b4-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7b4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b7b4-125">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7b4-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7b4-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b7b4-126">See Also</span></span>  
 [<span data-ttu-id="7b7b4-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7b7b4-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7b7b4-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="7b7b4-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
