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
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965637"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="5cc91-102">ICorDebugReferenceValue 介面</span><span class="sxs-lookup"><span data-stu-id="5cc91-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="5cc91-103">提供管理物件之參考值的方法。</span><span class="sxs-lookup"><span data-stu-id="5cc91-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="5cc91-104">(亦即, 此介面提供管理指標的方法)。此介面會執行 "ICorDebugValue"。</span><span class="sxs-lookup"><span data-stu-id="5cc91-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cc91-105">方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-105">Methods</span></span>  
  
|<span data-ttu-id="5cc91-106">方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-106">Method</span></span>|<span data-ttu-id="5cc91-107">描述</span><span class="sxs-lookup"><span data-stu-id="5cc91-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5cc91-108">Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="5cc91-109">取得所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="5cc91-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="5cc91-110">DereferenceStrong 方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="5cc91-111">未實作。</span><span class="sxs-lookup"><span data-stu-id="5cc91-111">Not implemented.</span></span> <span data-ttu-id="5cc91-112">請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="5cc91-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="5cc91-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="5cc91-114">取得受參考物件目前的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="5cc91-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="5cc91-115">IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="5cc91-116">取得值, 指出這`ICorDebugReferenceValue`是否為 null 值, 在此`ICorDebugReferenceValue`情況下, 不會指向物件。</span><span class="sxs-lookup"><span data-stu-id="5cc91-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="5cc91-117">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="5cc91-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="5cc91-118">設定目前的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="5cc91-118">Sets the current memory address.</span></span> <span data-ttu-id="5cc91-119">也就是說, 這個方法會將此`ICorDebugReferenceValue`設定為指向物件。</span><span class="sxs-lookup"><span data-stu-id="5cc91-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cc91-120">備註</span><span class="sxs-lookup"><span data-stu-id="5cc91-120">Remarks</span></span>  
 <span data-ttu-id="5cc91-121">通用語言執行平臺 (CLR) 可能會在已調試的進程繼續時, 對物件進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="5cc91-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="5cc91-122">垃圾收集可能會在記憶體中移動物件。</span><span class="sxs-lookup"><span data-stu-id="5cc91-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="5cc91-123">`ICorDebugReferenceValue`會與垃圾收集合作, 以便在垃圾收集之後更新其資訊, 或在垃圾收集之前隱含地將其視為無效。</span><span class="sxs-lookup"><span data-stu-id="5cc91-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="5cc91-124">繼續`ICorDebugReferenceValue`進行已調試的進程之後, 可能會隱含地使物件失效。</span><span class="sxs-lookup"><span data-stu-id="5cc91-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="5cc91-125">衍生的 "ICorDebugHandleValue" 在明確釋放或公開之前不會無效。</span><span class="sxs-lookup"><span data-stu-id="5cc91-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cc91-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5cc91-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc91-127">需求</span><span class="sxs-lookup"><span data-stu-id="5cc91-127">Requirements</span></span>  
 <span data-ttu-id="5cc91-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc91-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc91-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cc91-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cc91-130">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cc91-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cc91-131">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc91-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc91-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cc91-132">See also</span></span>

- [<span data-ttu-id="5cc91-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5cc91-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
