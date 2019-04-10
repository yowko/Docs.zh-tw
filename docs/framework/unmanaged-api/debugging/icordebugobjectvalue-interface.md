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
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222610"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="1c79d-102">ICorDebugObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="1c79d-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="1c79d-103">「 ICorDebugValue"，表示包含物件的值的子類別。</span><span class="sxs-lookup"><span data-stu-id="1c79d-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c79d-104">方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-104">Methods</span></span>  
  
|<span data-ttu-id="1c79d-105">方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-105">Method</span></span>|<span data-ttu-id="1c79d-106">描述</span><span class="sxs-lookup"><span data-stu-id="1c79d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c79d-107">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="1c79d-108">取得 common language runtime (CLR) 的介面指標<xref:System.Type>物件的這個`ICorDebugObjectValue`參考。</span><span class="sxs-lookup"><span data-stu-id="1c79d-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="1c79d-109">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="1c79d-110">未實作。</span><span class="sxs-lookup"><span data-stu-id="1c79d-110">Not implemented.</span></span>|  
|[<span data-ttu-id="1c79d-111">GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="1c79d-112">取得的介面指標[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) ，表示指定之類別的指定欄位的值。</span><span class="sxs-lookup"><span data-stu-id="1c79d-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="1c79d-113">GetManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="1c79d-114">已過時。</span><span class="sxs-lookup"><span data-stu-id="1c79d-114">Obsolete.</span></span> <span data-ttu-id="1c79d-115">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1c79d-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="1c79d-116">GetVirtualMethod 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="1c79d-117">未實作。</span><span class="sxs-lookup"><span data-stu-id="1c79d-117">Not implemented.</span></span>|  
|[<span data-ttu-id="1c79d-118">IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="1c79d-119">取得值，指出物件是否參考由此`ICorDebugObjectValue`是實值類型。</span><span class="sxs-lookup"><span data-stu-id="1c79d-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="1c79d-120">SetFromManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="1c79d-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="1c79d-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="1c79d-121">Obsolete.</span></span> <span data-ttu-id="1c79d-122">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1c79d-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c79d-123">備註</span><span class="sxs-lookup"><span data-stu-id="1c79d-123">Remarks</span></span>  
 <span data-ttu-id="1c79d-124">`ICorDebugObjectValue`維持有效，直到正在偵錯處理序會繼續。</span><span class="sxs-lookup"><span data-stu-id="1c79d-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c79d-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c79d-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c79d-126">需求</span><span class="sxs-lookup"><span data-stu-id="1c79d-126">Requirements</span></span>  
 <span data-ttu-id="1c79d-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c79d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c79d-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c79d-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c79d-129">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c79d-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1c79d-130">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1c79d-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c79d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c79d-131">See also</span></span>

- [<span data-ttu-id="1c79d-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1c79d-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
