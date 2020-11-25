---
title: ICorDebugExceptionDebugEvent::GetNativeIP 方法
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: f3b29b3ceda521afe9543588af332531aa03e84e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697411"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="0d1dd-102">ICorDebugExceptionDebugEvent::GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="0d1dd-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>

<span data-ttu-id="0d1dd-103">取得這個例外狀況偵錯事件的原生指令指標。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d1dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d1dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d1dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d1dd-105">Parameters</span></span>  

 `pIP`  
 <span data-ttu-id="0d1dd-106">[out] 這個例外狀況偵錯事件之指令指標的指標。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="0d1dd-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d1dd-108">備註</span><span class="sxs-lookup"><span data-stu-id="0d1dd-108">Remarks</span></span>  

 <span data-ttu-id="0d1dd-109">這個指令指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0d1dd-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="0d1dd-110">Event type</span></span>|<span data-ttu-id="0d1dd-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="0d1dd-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="0d1dd-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0d1dd-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="0d1dd-113">失敗指令的位址。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="0d1dd-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0d1dd-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="0d1dd-115">[GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md)方法所指出的框架中的程式碼位址，如果未引發任何例外狀況，則會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="0d1dd-116">例外狀況不一定會在這個框架中執行不同的程式碼 (例如 `try/catch/finally` 子句的 catch 區塊)。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="0d1dd-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="0d1dd-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="0d1dd-118">`catch`處理常式執行將在[GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md)方法所指出的框架中開始的程式碼位址。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="0d1dd-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="0d1dd-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="0d1dd-120">`pIP` 為 0。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="0d1dd-121">您可以從 [ICorDebugDebugEvent：： GetEventKind](icordebugdebugevent-geteventkind-method.md) 方法取得事件種類。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d1dd-122">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d1dd-123">需求</span><span class="sxs-lookup"><span data-stu-id="0d1dd-123">Requirements</span></span>  

 <span data-ttu-id="0d1dd-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d1dd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d1dd-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d1dd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d1dd-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d1dd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d1dd-127">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d1dd-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1dd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d1dd-128">See also</span></span>

- [<span data-ttu-id="0d1dd-129">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0d1dd-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="0d1dd-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0d1dd-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
