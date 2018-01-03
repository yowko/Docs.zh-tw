---
title: ICorDebugValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue
helpviewer_keywords: ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="67689-102">ICorDebugValue Interface1</span><span class="sxs-lookup"><span data-stu-id="67689-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="67689-103">表示正在進行偵錯的處理序中的值。</span><span class="sxs-lookup"><span data-stu-id="67689-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="67689-104">值可以是讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="67689-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67689-105">方法</span><span class="sxs-lookup"><span data-stu-id="67689-105">Methods</span></span>  
  
|<span data-ttu-id="67689-106">方法</span><span class="sxs-lookup"><span data-stu-id="67689-106">Method</span></span>|<span data-ttu-id="67689-107">描述</span><span class="sxs-lookup"><span data-stu-id="67689-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67689-108">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="67689-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="67689-109">目前尚未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="67689-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="67689-110">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="67689-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="67689-111">取得這個位址`ICorDebugValue`物件，它是正在進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="67689-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="67689-112">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="67689-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="67689-113">取得以位元組為單位，這個大小，`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="67689-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="67689-114">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="67689-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="67689-115">取得這個的基本型別`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="67689-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67689-116">備註</span><span class="sxs-lookup"><span data-stu-id="67689-116">Remarks</span></span>  
 <span data-ttu-id="67689-117">一般情況下，當它傳回時，會傳遞值物件的擁有權。</span><span class="sxs-lookup"><span data-stu-id="67689-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="67689-118">收件者會負責在物件完成時，從物件移除參考。</span><span class="sxs-lookup"><span data-stu-id="67689-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="67689-119">根據位置已從擷取的值，值可能不會維持有效之後繼續此程序。</span><span class="sxs-lookup"><span data-stu-id="67689-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="67689-120">因此，在一般情況下，值不應該保留跨的呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="67689-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67689-121">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="67689-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67689-122">需求</span><span class="sxs-lookup"><span data-stu-id="67689-122">Requirements</span></span>  
 <span data-ttu-id="67689-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67689-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67689-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67689-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67689-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67689-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67689-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67689-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67689-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="67689-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="67689-128">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="67689-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="67689-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="67689-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
