---
title: "ICorDebugExceptionDebugEvent::GetNativeIP 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32e75a18645c000562cdd94478c6ef8db41a01a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="d7bb2-102">ICorDebugExceptionDebugEvent::GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="d7bb2-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="d7bb2-103">取得這個例外狀況偵錯事件的原生指令指標。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7bb2-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7bb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7bb2-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="d7bb2-106">[out] 這個例外狀況偵錯事件之指令指標的指標。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="d7bb2-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7bb2-108">備註</span><span class="sxs-lookup"><span data-stu-id="d7bb2-108">Remarks</span></span>  
 <span data-ttu-id="d7bb2-109">這個指令指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d7bb2-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="d7bb2-110">Event type</span></span>|<span data-ttu-id="d7bb2-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="d7bb2-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="d7bb2-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d7bb2-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="d7bb2-113">失敗指令的位址。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="d7bb2-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d7bb2-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="d7bb2-115">在框架中的程式碼位址所指定[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)如果不引發任何例外狀況則會繼續執行的所在方法。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="d7bb2-116">例外狀況不一定會在這個框架中執行不同的程式碼 (例如 `try/catch/finally` 子句的 catch 區塊)。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="d7bb2-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="d7bb2-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="d7bb2-118">程式碼位址，其中`catch`中表示的框架將開始的處理常式執行[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="d7bb2-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="d7bb2-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="d7bb2-120">`pIP` 為 0。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="d7bb2-121">事件類型是由[icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7bb2-122">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7bb2-123">需求</span><span class="sxs-lookup"><span data-stu-id="d7bb2-123">Requirements</span></span>  
 <span data-ttu-id="d7bb2-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7bb2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7bb2-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7bb2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7bb2-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7bb2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7bb2-127">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7bb2-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bb2-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7bb2-128">See Also</span></span>  
 [<span data-ttu-id="d7bb2-129">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d7bb2-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="d7bb2-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d7bb2-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
