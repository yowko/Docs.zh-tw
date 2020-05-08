---
title: ICorDebugExceptionDebugEvent::GetStackPointer 方法
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 4f84183dfc23ebc0d0fee9feeb21329c217b9cca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976014"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="07358-102">ICorDebugExceptionDebugEvent::GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="07358-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="07358-103">取得這個例外狀況偵錯事件的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="07358-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07358-104">語法</span><span class="sxs-lookup"><span data-stu-id="07358-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07358-105">參數</span><span class="sxs-lookup"><span data-stu-id="07358-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="07358-106">[out] 這個例外狀況偵錯事件之堆疊指標的位址指標。</span><span class="sxs-lookup"><span data-stu-id="07358-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="07358-107">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="07358-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07358-108">備註</span><span class="sxs-lookup"><span data-stu-id="07358-108">Remarks</span></span>  
 <span data-ttu-id="07358-109">這個堆疊指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="07358-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="07358-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="07358-110">Event type</span></span>|<span data-ttu-id="07358-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="07358-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="07358-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="07358-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="07358-113">擲回例外狀況之框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="07358-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="07358-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="07358-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="07358-115">最接近擲回例外狀況位置之使用者程式碼框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="07358-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="07358-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="07358-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="07358-117">包含 catch 處理常式之框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="07358-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="07358-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="07358-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="07358-119">`pStackPointer` 為 **null**。</span><span class="sxs-lookup"><span data-stu-id="07358-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="07358-120">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="07358-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="07358-121">事件種類可從[ICorDebugDebugEvent：： GetEventKind](icordebugdebugevent-geteventkind-method.md)方法取得。</span><span class="sxs-lookup"><span data-stu-id="07358-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07358-122">需求</span><span class="sxs-lookup"><span data-stu-id="07358-122">Requirements</span></span>  
 <span data-ttu-id="07358-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07358-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07358-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07358-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07358-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07358-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07358-126">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07358-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07358-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07358-127">See also</span></span>

- [<span data-ttu-id="07358-128">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="07358-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="07358-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="07358-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
