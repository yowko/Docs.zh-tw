---
title: ICorDebugExceptionDebugEvent::GetStackPointer 方法
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4c0a1938edd3e2fe88ea6e418b3430f1b5cb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163198"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="193ef-102">ICorDebugExceptionDebugEvent::GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="193ef-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="193ef-103">取得這個例外狀況偵錯事件的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="193ef-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="193ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="193ef-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="193ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="193ef-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="193ef-106">[out] 這個例外狀況偵錯事件之堆疊指標的位址指標。</span><span class="sxs-lookup"><span data-stu-id="193ef-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="193ef-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="193ef-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="193ef-108">備註</span><span class="sxs-lookup"><span data-stu-id="193ef-108">Remarks</span></span>  
 <span data-ttu-id="193ef-109">這個堆疊指標的意義取決於事件類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="193ef-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="193ef-110">事件類型</span><span class="sxs-lookup"><span data-stu-id="193ef-110">Event type</span></span>|<span data-ttu-id="193ef-111">`pStackPointer` 值的意義</span><span class="sxs-lookup"><span data-stu-id="193ef-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="193ef-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="193ef-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="193ef-113">擲回例外狀況之框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="193ef-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="193ef-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="193ef-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="193ef-115">最接近擲回例外狀況位置之使用者程式碼框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="193ef-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="193ef-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="193ef-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="193ef-117">包含 catch 處理常式之框架的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="193ef-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="193ef-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="193ef-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer` <span data-ttu-id="193ef-119">已**null**。</span><span class="sxs-lookup"><span data-stu-id="193ef-119">is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="193ef-120">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="193ef-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="193ef-121">事件類型是由[icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="193ef-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="193ef-122">需求</span><span class="sxs-lookup"><span data-stu-id="193ef-122">Requirements</span></span>  
 <span data-ttu-id="193ef-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="193ef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="193ef-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="193ef-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="193ef-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="193ef-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="193ef-126">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="193ef-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="193ef-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="193ef-127">See also</span></span>

- [<span data-ttu-id="193ef-128">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="193ef-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="193ef-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="193ef-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
