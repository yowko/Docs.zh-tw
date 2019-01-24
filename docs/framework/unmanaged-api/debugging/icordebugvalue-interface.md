---
title: ICorDebugValue 介面 1
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41afc2e4305034340ad408e52ce08372bf8962dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507443"
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="58159-102">ICorDebugValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="58159-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="58159-103">表示正在進行偵錯程序中的值。</span><span class="sxs-lookup"><span data-stu-id="58159-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="58159-104">值可以是讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="58159-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58159-105">方法</span><span class="sxs-lookup"><span data-stu-id="58159-105">Methods</span></span>  
  
|<span data-ttu-id="58159-106">方法</span><span class="sxs-lookup"><span data-stu-id="58159-106">Method</span></span>|<span data-ttu-id="58159-107">描述</span><span class="sxs-lookup"><span data-stu-id="58159-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58159-108">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="58159-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="58159-109">這個方法目前尚未實作。</span><span class="sxs-lookup"><span data-stu-id="58159-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="58159-110">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="58159-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="58159-111">取得這個位址`ICorDebugValue`物件，這是正在進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="58159-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="58159-112">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="58159-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="58159-113">取得大小，以位元組為單位，這個`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="58159-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="58159-114">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="58159-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="58159-115">取得這個基本型別`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="58159-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58159-116">備註</span><span class="sxs-lookup"><span data-stu-id="58159-116">Remarks</span></span>  
 <span data-ttu-id="58159-117">一般情況下，它會傳回時，會傳遞值物件的擁有權。</span><span class="sxs-lookup"><span data-stu-id="58159-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="58159-118">收件者會負責與物件完成時，從物件移除參考。</span><span class="sxs-lookup"><span data-stu-id="58159-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="58159-119">根據位置已從擷取的值，值可能不會維持有效之後繼續此程序。</span><span class="sxs-lookup"><span data-stu-id="58159-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="58159-120">因此，在一般情況下，保留的值不應該呼叫跨越[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="58159-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58159-121">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="58159-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58159-122">需求</span><span class="sxs-lookup"><span data-stu-id="58159-122">Requirements</span></span>  
 <span data-ttu-id="58159-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58159-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58159-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58159-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58159-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58159-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58159-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58159-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58159-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58159-127">See also</span></span>




- [<span data-ttu-id="58159-128">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="58159-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="58159-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58159-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
