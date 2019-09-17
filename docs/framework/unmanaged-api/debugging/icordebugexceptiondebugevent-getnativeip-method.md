---
title: ICorDebugExceptionDebugEvent::GetNativeIP 方法
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa1a160bb316831540f68713647dbdc4b0f6895
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951843"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="befbb-102">ICorDebugExceptionDebugEvent::GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="befbb-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="befbb-103">取得這個例外狀況偵錯事件的原生指令指標。</span><span class="sxs-lookup"><span data-stu-id="befbb-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="befbb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="befbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="befbb-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="befbb-106">[out] 這個例外狀況偵錯事件之指令指標的指標。</span><span class="sxs-lookup"><span data-stu-id="befbb-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="befbb-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="befbb-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="befbb-108">備註</span><span class="sxs-lookup"><span data-stu-id="befbb-108">Remarks</span></span>  
 <span data-ttu-id="befbb-109">這個指令指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="befbb-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="befbb-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="befbb-110">Event type</span></span>|<span data-ttu-id="befbb-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="befbb-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="befbb-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="befbb-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="befbb-113">失敗指令的位址。</span><span class="sxs-lookup"><span data-stu-id="befbb-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="befbb-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="befbb-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="befbb-115">[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)方法所表示的框架中的程式碼位址，如果未引發任何例外狀況，則執行會繼續。</span><span class="sxs-lookup"><span data-stu-id="befbb-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="befbb-116">例外狀況不一定會在這個框架中執行不同的程式碼 (例如 `try/catch/finally` 子句的 catch 區塊)。</span><span class="sxs-lookup"><span data-stu-id="befbb-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="befbb-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="befbb-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="befbb-118">在 [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) 方法所指示的框架中，`catch`處理常式執行將在其中啟動的程式碼位址。</span><span class="sxs-lookup"><span data-stu-id="befbb-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="befbb-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="befbb-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="befbb-120">`pIP` 為 0。</span><span class="sxs-lookup"><span data-stu-id="befbb-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="befbb-121">事件種類可從[ICorDebugDebugEvent：： GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法取得。</span><span class="sxs-lookup"><span data-stu-id="befbb-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="befbb-122">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="befbb-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="befbb-123">需求</span><span class="sxs-lookup"><span data-stu-id="befbb-123">Requirements</span></span>  
 <span data-ttu-id="befbb-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="befbb-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="befbb-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="befbb-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="befbb-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="befbb-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="befbb-127">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="befbb-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befbb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="befbb-128">See also</span></span>

- [<span data-ttu-id="befbb-129">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="befbb-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="befbb-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="befbb-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
