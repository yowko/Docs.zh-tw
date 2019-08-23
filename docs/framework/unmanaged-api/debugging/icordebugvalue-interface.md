---
title: ICorDebugValue 介面
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
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966867"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="9fc09-102">ICorDebugValue 介面</span><span class="sxs-lookup"><span data-stu-id="9fc09-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="9fc09-103">表示正在進行調試之進程中的值。</span><span class="sxs-lookup"><span data-stu-id="9fc09-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="9fc09-104">此值可以是讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="9fc09-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fc09-105">方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-105">Methods</span></span>  
  
|<span data-ttu-id="9fc09-106">方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-106">Method</span></span>|<span data-ttu-id="9fc09-107">描述</span><span class="sxs-lookup"><span data-stu-id="9fc09-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fc09-108">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="9fc09-109">這個方法目前未執行。</span><span class="sxs-lookup"><span data-stu-id="9fc09-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="9fc09-110">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="9fc09-111">取得此物件的位址`ICorDebugValue` , 此為正在進行調試的進程。</span><span class="sxs-lookup"><span data-stu-id="9fc09-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="9fc09-112">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="9fc09-113">取得這個`ICorDebugValue`物件的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="9fc09-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="9fc09-114">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="9fc09-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="9fc09-115">取得此`ICorDebugValue`物件的基本類型。</span><span class="sxs-lookup"><span data-stu-id="9fc09-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fc09-116">備註</span><span class="sxs-lookup"><span data-stu-id="9fc09-116">Remarks</span></span>  
 <span data-ttu-id="9fc09-117">一般情況下, 值物件的擁有權會在傳回時傳遞。</span><span class="sxs-lookup"><span data-stu-id="9fc09-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="9fc09-118">當物件完成時, 收件者會負責從物件中移除參考。</span><span class="sxs-lookup"><span data-stu-id="9fc09-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="9fc09-119">根據從其中抓取值的位置而定, 此值在進程繼續之後可能不會保持有效。</span><span class="sxs-lookup"><span data-stu-id="9fc09-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="9fc09-120">因此, 一般而言, 此值不應保留在[ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法的呼叫中。</span><span class="sxs-lookup"><span data-stu-id="9fc09-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fc09-121">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9fc09-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc09-122">需求</span><span class="sxs-lookup"><span data-stu-id="9fc09-122">Requirements</span></span>  
 <span data-ttu-id="9fc09-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fc09-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc09-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fc09-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fc09-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fc09-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fc09-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc09-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc09-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc09-127">See also</span></span>

- [<span data-ttu-id="9fc09-128">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="9fc09-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="9fc09-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9fc09-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
