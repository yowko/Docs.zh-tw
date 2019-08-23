---
title: ICorDebugObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943327"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="5e750-102">ICorDebugObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="5e750-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="5e750-103">"ICorDebugValue" 的子類別, 表示包含物件的值。</span><span class="sxs-lookup"><span data-stu-id="5e750-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e750-104">方法</span><span class="sxs-lookup"><span data-stu-id="5e750-104">Methods</span></span>  
  
|<span data-ttu-id="5e750-105">方法</span><span class="sxs-lookup"><span data-stu-id="5e750-105">Method</span></span>|<span data-ttu-id="5e750-106">描述</span><span class="sxs-lookup"><span data-stu-id="5e750-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e750-107">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="5e750-108">取得這個<xref:System.Type> `ICorDebugObjectValue`所參考物件之通用語言執行時間 (CLR) 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="5e750-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="5e750-109">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="5e750-110">未實作。</span><span class="sxs-lookup"><span data-stu-id="5e750-110">Not implemented.</span></span>|  
|[<span data-ttu-id="5e750-111">GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="5e750-112">取得[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)的介面指標, 表示指定類別之指定欄位的值。</span><span class="sxs-lookup"><span data-stu-id="5e750-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="5e750-113">GetManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="5e750-114">已過時。</span><span class="sxs-lookup"><span data-stu-id="5e750-114">Obsolete.</span></span> <span data-ttu-id="5e750-115">請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="5e750-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="5e750-116">GetVirtualMethod 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="5e750-117">未實作。</span><span class="sxs-lookup"><span data-stu-id="5e750-117">Not implemented.</span></span>|  
|[<span data-ttu-id="5e750-118">IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="5e750-119">取得值, 指出這個`ICorDebugObjectValue`所參考的物件是否為實值型別。</span><span class="sxs-lookup"><span data-stu-id="5e750-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="5e750-120">SetFromManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="5e750-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="5e750-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="5e750-121">Obsolete.</span></span> <span data-ttu-id="5e750-122">請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="5e750-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e750-123">備註</span><span class="sxs-lookup"><span data-stu-id="5e750-123">Remarks</span></span>  
 <span data-ttu-id="5e750-124">會`ICorDebugObjectValue`維持有效, 直到正在進行調試的進程繼續為止。</span><span class="sxs-lookup"><span data-stu-id="5e750-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e750-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5e750-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e750-126">需求</span><span class="sxs-lookup"><span data-stu-id="5e750-126">Requirements</span></span>  
 <span data-ttu-id="5e750-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e750-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e750-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e750-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e750-129">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e750-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e750-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e750-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e750-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e750-131">See also</span></span>

- [<span data-ttu-id="5e750-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5e750-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
