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
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207485"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="36034-102">ICorDebugObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="36034-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="36034-103">"ICorDebugValue" 的子類別，表示包含物件的值。</span><span class="sxs-lookup"><span data-stu-id="36034-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36034-104">方法</span><span class="sxs-lookup"><span data-stu-id="36034-104">Methods</span></span>  
  
|<span data-ttu-id="36034-105">方法</span><span class="sxs-lookup"><span data-stu-id="36034-105">Method</span></span>|<span data-ttu-id="36034-106">描述</span><span class="sxs-lookup"><span data-stu-id="36034-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36034-107">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="36034-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="36034-108">取得 <xref:System.Type> 這個所參考物件之通用語言執行時間（CLR）的介面指標 `ICorDebugObjectValue` 。</span><span class="sxs-lookup"><span data-stu-id="36034-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="36034-109">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="36034-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="36034-110">未實作。</span><span class="sxs-lookup"><span data-stu-id="36034-110">Not implemented.</span></span>|  
|[<span data-ttu-id="36034-111">GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="36034-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="36034-112">取得[ICorDebugValue](icordebugvalue-interface.md)的介面指標，表示指定類別之指定欄位的值。</span><span class="sxs-lookup"><span data-stu-id="36034-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="36034-113">GetManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="36034-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="36034-114">已過時。</span><span class="sxs-lookup"><span data-stu-id="36034-114">Obsolete.</span></span> <span data-ttu-id="36034-115">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="36034-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="36034-116">GetVirtualMethod 方法</span><span class="sxs-lookup"><span data-stu-id="36034-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="36034-117">未實作。</span><span class="sxs-lookup"><span data-stu-id="36034-117">Not implemented.</span></span>|  
|[<span data-ttu-id="36034-118">IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="36034-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="36034-119">取得值，指出這個所參考的物件是否 `ICorDebugObjectValue` 為實值型別。</span><span class="sxs-lookup"><span data-stu-id="36034-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="36034-120">SetFromManagedCopy 方法</span><span class="sxs-lookup"><span data-stu-id="36034-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="36034-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="36034-121">Obsolete.</span></span> <span data-ttu-id="36034-122">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="36034-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36034-123">備註</span><span class="sxs-lookup"><span data-stu-id="36034-123">Remarks</span></span>  
 <span data-ttu-id="36034-124">`ICorDebugObjectValue`會維持有效，直到正在進行調試的進程繼續為止。</span><span class="sxs-lookup"><span data-stu-id="36034-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36034-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="36034-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36034-126">需求</span><span class="sxs-lookup"><span data-stu-id="36034-126">Requirements</span></span>  
 <span data-ttu-id="36034-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36034-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36034-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36034-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36034-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36034-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36034-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36034-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36034-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="36034-131">See also</span></span>

- [<span data-ttu-id="36034-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="36034-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
