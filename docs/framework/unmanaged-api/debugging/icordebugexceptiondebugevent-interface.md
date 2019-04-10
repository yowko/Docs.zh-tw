---
title: ICorDebugExceptionDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e2a147d46412eb4feb192070ff8420cab842a6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156451"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="661ca-102">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="661ca-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="661ca-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="661ca-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="661ca-104">方法</span><span class="sxs-lookup"><span data-stu-id="661ca-104">Methods</span></span>  
  
|<span data-ttu-id="661ca-105">方法</span><span class="sxs-lookup"><span data-stu-id="661ca-105">Method</span></span>|<span data-ttu-id="661ca-106">描述</span><span class="sxs-lookup"><span data-stu-id="661ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="661ca-107">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="661ca-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="661ca-108">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="661ca-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="661ca-109">GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="661ca-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="661ca-110">取得這個例外狀況偵錯事件的原生介面指標。</span><span class="sxs-lookup"><span data-stu-id="661ca-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="661ca-111">GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="661ca-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="661ca-112">取得這個例外狀況偵錯事件的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="661ca-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="661ca-113">備註</span><span class="sxs-lookup"><span data-stu-id="661ca-113">Remarks</span></span>  
 <span data-ttu-id="661ca-114">`ICorDebugExceptionDebugEvent` 介面由下列事件類型實作：</span><span class="sxs-lookup"><span data-stu-id="661ca-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="661ca-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="661ca-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="661ca-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="661ca-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="661ca-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="661ca-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="661ca-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="661ca-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="661ca-119">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="661ca-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="661ca-120">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="661ca-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661ca-121">需求</span><span class="sxs-lookup"><span data-stu-id="661ca-121">Requirements</span></span>  
 <span data-ttu-id="661ca-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="661ca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661ca-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="661ca-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="661ca-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="661ca-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="661ca-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="661ca-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="661ca-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="661ca-126">See also</span></span>

- [<span data-ttu-id="661ca-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="661ca-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="661ca-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="661ca-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
