---
title: ICorDebugReferenceValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6575acfb1f75cbc8e3d59ddca5fea0953274cf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782950"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="849c8-102">ICorDebugReferenceValue 介面</span><span class="sxs-lookup"><span data-stu-id="849c8-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="849c8-103">提供方法，可管理的參考物件的值。</span><span class="sxs-lookup"><span data-stu-id="849c8-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="849c8-104">（也就是這個介面提供管理指標的方法）。這個介面會實作 「 ICorDebugValue"。</span><span class="sxs-lookup"><span data-stu-id="849c8-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="849c8-105">方法</span><span class="sxs-lookup"><span data-stu-id="849c8-105">Methods</span></span>  
  
|<span data-ttu-id="849c8-106">方法</span><span class="sxs-lookup"><span data-stu-id="849c8-106">Method</span></span>|<span data-ttu-id="849c8-107">描述</span><span class="sxs-lookup"><span data-stu-id="849c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="849c8-108">Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="849c8-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="849c8-109">取得參考的物件。</span><span class="sxs-lookup"><span data-stu-id="849c8-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="849c8-110">DereferenceStrong 方法</span><span class="sxs-lookup"><span data-stu-id="849c8-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="849c8-111">未實作。</span><span class="sxs-lookup"><span data-stu-id="849c8-111">Not implemented.</span></span> <span data-ttu-id="849c8-112">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="849c8-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="849c8-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="849c8-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="849c8-114">取得參考物件的目前記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="849c8-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="849c8-115">IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="849c8-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="849c8-116">取得值，指出是否這`ICorDebugReferenceValue`為 null 值，在此情況下`ICorDebugReferenceValue`未指向物件。</span><span class="sxs-lookup"><span data-stu-id="849c8-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="849c8-117">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="849c8-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="849c8-118">設定目前的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="849c8-118">Sets the current memory address.</span></span> <span data-ttu-id="849c8-119">也就是說，這個方法會設定這個`ICorDebugReferenceValue`指向物件。</span><span class="sxs-lookup"><span data-stu-id="849c8-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="849c8-120">備註</span><span class="sxs-lookup"><span data-stu-id="849c8-120">Remarks</span></span>  
 <span data-ttu-id="849c8-121">Common language runtime (CLR) 偵錯的處理序會繼續時，可以執行回收物件。</span><span class="sxs-lookup"><span data-stu-id="849c8-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="849c8-122">記憶體回收可能會移動物件在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="849c8-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="849c8-123">`ICorDebugReferenceValue`會是與合作的記憶體回收，讓記憶體回收之後, 會更新其資訊，或它之前的記憶體回收會以隱含方式失效。</span><span class="sxs-lookup"><span data-stu-id="849c8-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="849c8-124">`ICorDebugReferenceValue`物件可能會因為隱含失效之後繼續執行偵錯的處理序。</span><span class="sxs-lookup"><span data-stu-id="849c8-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="849c8-125">衍生的 」 ICorDebugHandleValue 」 不會失效，直到明確釋放或公開。</span><span class="sxs-lookup"><span data-stu-id="849c8-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="849c8-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="849c8-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849c8-127">需求</span><span class="sxs-lookup"><span data-stu-id="849c8-127">Requirements</span></span>  
 <span data-ttu-id="849c8-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="849c8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849c8-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="849c8-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="849c8-130">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="849c8-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="849c8-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849c8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849c8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="849c8-132">See also</span></span>

- [<span data-ttu-id="849c8-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="849c8-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
