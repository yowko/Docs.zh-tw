---
title: ICorDebugExceptionDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e2a147d46412eb4feb192070ff8420cab842a6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995882"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="32b57-102">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="32b57-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="32b57-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="32b57-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32b57-104">方法</span><span class="sxs-lookup"><span data-stu-id="32b57-104">Methods</span></span>  
  
|<span data-ttu-id="32b57-105">方法</span><span class="sxs-lookup"><span data-stu-id="32b57-105">Method</span></span>|<span data-ttu-id="32b57-106">描述</span><span class="sxs-lookup"><span data-stu-id="32b57-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32b57-107">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="32b57-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="32b57-108">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="32b57-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="32b57-109">GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="32b57-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="32b57-110">取得這個例外狀況偵錯事件的原生介面指標。</span><span class="sxs-lookup"><span data-stu-id="32b57-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="32b57-111">GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="32b57-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="32b57-112">取得這個例外狀況偵錯事件的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="32b57-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32b57-113">備註</span><span class="sxs-lookup"><span data-stu-id="32b57-113">Remarks</span></span>  
 <span data-ttu-id="32b57-114">`ICorDebugExceptionDebugEvent` 介面由下列事件類型實作：</span><span class="sxs-lookup"><span data-stu-id="32b57-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="32b57-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="32b57-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="32b57-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="32b57-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="32b57-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="32b57-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="32b57-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="32b57-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="32b57-119">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="32b57-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="32b57-120">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="32b57-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b57-121">需求</span><span class="sxs-lookup"><span data-stu-id="32b57-121">Requirements</span></span>  
 <span data-ttu-id="32b57-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32b57-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b57-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32b57-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32b57-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32b57-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b57-125">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b57-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b57-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b57-126">See also</span></span>

- [<span data-ttu-id="32b57-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="32b57-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="32b57-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="32b57-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
