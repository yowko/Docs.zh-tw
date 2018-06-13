---
title: ICorDebugObjectValue Interface1
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
ms.openlocfilehash: 7ddf3b60ed595aff8bc81d0bb59675fd1db12f7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422409"
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="67eda-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="67eda-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="67eda-103">「 ICorDebugValue"，表示包含物件的值的子類別。</span><span class="sxs-lookup"><span data-stu-id="67eda-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67eda-104">方法</span><span class="sxs-lookup"><span data-stu-id="67eda-104">Methods</span></span>  
  
|<span data-ttu-id="67eda-105">方法</span><span class="sxs-lookup"><span data-stu-id="67eda-105">Method</span></span>|<span data-ttu-id="67eda-106">描述</span><span class="sxs-lookup"><span data-stu-id="67eda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67eda-107">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="67eda-108">Common language runtime (CLR) 中取得的介面指標<xref:System.Type>物件的這個`ICorDebugObjectValue`參考。</span><span class="sxs-lookup"><span data-stu-id="67eda-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="67eda-109">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="67eda-110">未實作。</span><span class="sxs-lookup"><span data-stu-id="67eda-110">Not implemented.</span></span>|  
|[<span data-ttu-id="67eda-111">GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="67eda-112">取得的介面指標[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)表示指定類別的指定之欄位的值。</span><span class="sxs-lookup"><span data-stu-id="67eda-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="67eda-113">GetManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="67eda-114">已過時。</span><span class="sxs-lookup"><span data-stu-id="67eda-114">Obsolete.</span></span> <span data-ttu-id="67eda-115">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="67eda-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="67eda-116">GetVirtualMethod 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="67eda-117">未實作。</span><span class="sxs-lookup"><span data-stu-id="67eda-117">Not implemented.</span></span>|  
|[<span data-ttu-id="67eda-118">IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="67eda-119">取得值，指出物件是否參考由此`ICorDebugObjectValue`是實值類型。</span><span class="sxs-lookup"><span data-stu-id="67eda-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="67eda-120">SetFromManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="67eda-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="67eda-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="67eda-121">Obsolete.</span></span> <span data-ttu-id="67eda-122">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="67eda-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67eda-123">備註</span><span class="sxs-lookup"><span data-stu-id="67eda-123">Remarks</span></span>  
 <span data-ttu-id="67eda-124">`ICorDebugObjectValue`就持續有效，直到進行偵錯處理序會繼續。</span><span class="sxs-lookup"><span data-stu-id="67eda-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67eda-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="67eda-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67eda-126">需求</span><span class="sxs-lookup"><span data-stu-id="67eda-126">Requirements</span></span>  
 <span data-ttu-id="67eda-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67eda-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67eda-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67eda-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67eda-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67eda-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67eda-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67eda-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67eda-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67eda-131">See Also</span></span>  
 [<span data-ttu-id="67eda-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="67eda-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
