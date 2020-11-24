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
ms.openlocfilehash: 7d3c35ed6cda637e3b885afe089ddfa590d51076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683598"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="9d9de-102">ICorDebugValue 介面</span><span class="sxs-lookup"><span data-stu-id="9d9de-102">ICorDebugValue Interface</span></span>

<span data-ttu-id="9d9de-103">表示正在進行調試之進程中的值。</span><span class="sxs-lookup"><span data-stu-id="9d9de-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="9d9de-104">值可以是讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="9d9de-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d9de-105">方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-105">Methods</span></span>  
  
|<span data-ttu-id="9d9de-106">方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-106">Method</span></span>|<span data-ttu-id="9d9de-107">描述</span><span class="sxs-lookup"><span data-stu-id="9d9de-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d9de-108">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="9d9de-109">這個方法目前尚未實作。</span><span class="sxs-lookup"><span data-stu-id="9d9de-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="9d9de-110">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="9d9de-111">取得此物件的位址 `ICorDebugValue` ，這個物件正在進行正在進行的處理。</span><span class="sxs-lookup"><span data-stu-id="9d9de-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="9d9de-112">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="9d9de-113">取得此物件的大小（以位元組為單位） `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="9d9de-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="9d9de-114">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="9d9de-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="9d9de-115">取得此物件的基本類型 `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="9d9de-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d9de-116">備註</span><span class="sxs-lookup"><span data-stu-id="9d9de-116">Remarks</span></span>  

 <span data-ttu-id="9d9de-117">一般情況下，值物件的擁有權會在傳回時傳遞。</span><span class="sxs-lookup"><span data-stu-id="9d9de-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="9d9de-118">當物件完成物件時，收件者會負責移除物件的參考。</span><span class="sxs-lookup"><span data-stu-id="9d9de-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="9d9de-119">根據從中抓取值的位置而定，此值在進程繼續之後可能不會保持有效。</span><span class="sxs-lookup"><span data-stu-id="9d9de-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="9d9de-120">因此，一般而言，此值不應該跨 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 方法的呼叫來保存。</span><span class="sxs-lookup"><span data-stu-id="9d9de-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d9de-121">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9d9de-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d9de-122">需求</span><span class="sxs-lookup"><span data-stu-id="9d9de-122">Requirements</span></span>  

 <span data-ttu-id="9d9de-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9de-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d9de-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d9de-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d9de-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d9de-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d9de-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9de-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9de-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d9de-127">See also</span></span>

- [<span data-ttu-id="9d9de-128">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="9d9de-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="9d9de-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9d9de-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
