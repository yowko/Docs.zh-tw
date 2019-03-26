---
title: ICorDebugExceptionDebugEvent::GetNativeIP 方法
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0069f301df9908a584608c7d20e5348de47361c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501600"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="30776-102">ICorDebugExceptionDebugEvent::GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="30776-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="30776-103">取得這個例外狀況偵錯事件的原生指令指標。</span><span class="sxs-lookup"><span data-stu-id="30776-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30776-104">語法</span><span class="sxs-lookup"><span data-stu-id="30776-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30776-105">參數</span><span class="sxs-lookup"><span data-stu-id="30776-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="30776-106">[out] 這個例外狀況偵錯事件之指令指標的指標。</span><span class="sxs-lookup"><span data-stu-id="30776-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="30776-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="30776-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30776-108">備註</span><span class="sxs-lookup"><span data-stu-id="30776-108">Remarks</span></span>  
 <span data-ttu-id="30776-109">這個指令指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="30776-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="30776-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="30776-110">Event type</span></span>|<span data-ttu-id="30776-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="30776-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="30776-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="30776-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="30776-113">失敗指令的位址。</span><span class="sxs-lookup"><span data-stu-id="30776-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="30776-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="30776-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="30776-115">在框架中的程式碼位址由[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)會繼續執行如果不引發任何例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="30776-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="30776-116">例外狀況不一定會在這個框架中執行不同的程式碼 (例如 `try/catch/finally` 子句的 catch 區塊)。</span><span class="sxs-lookup"><span data-stu-id="30776-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="30776-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="30776-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="30776-118">程式碼位址，其中`catch`中所指示的畫面格會開始處理常式執行[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="30776-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="30776-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="30776-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="30776-120">`pIP` 為 0。</span><span class="sxs-lookup"><span data-stu-id="30776-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="30776-121">事件類型是由[icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="30776-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30776-122">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="30776-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30776-123">需求</span><span class="sxs-lookup"><span data-stu-id="30776-123">Requirements</span></span>  
 <span data-ttu-id="30776-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30776-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30776-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30776-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30776-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30776-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30776-127">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30776-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30776-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30776-128">See also</span></span>
- [<span data-ttu-id="30776-129">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="30776-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="30776-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="30776-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
