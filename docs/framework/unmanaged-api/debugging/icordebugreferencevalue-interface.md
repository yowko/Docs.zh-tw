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
ms.openlocfilehash: 6c6ff428e378e973d8846674ffacdcd04b2dbdbc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378352"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="28578-102">ICorDebugReferenceValue 介面</span><span class="sxs-lookup"><span data-stu-id="28578-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="28578-103">提供管理物件之參考值的方法。</span><span class="sxs-lookup"><span data-stu-id="28578-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="28578-104">（亦即，此介面提供管理指標的方法）。此介面會執行 "ICorDebugValue"。</span><span class="sxs-lookup"><span data-stu-id="28578-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28578-105">方法</span><span class="sxs-lookup"><span data-stu-id="28578-105">Methods</span></span>  
  
|<span data-ttu-id="28578-106">方法</span><span class="sxs-lookup"><span data-stu-id="28578-106">Method</span></span>|<span data-ttu-id="28578-107">描述</span><span class="sxs-lookup"><span data-stu-id="28578-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28578-108">Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="28578-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="28578-109">取得所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="28578-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="28578-110">DereferenceStrong 方法</span><span class="sxs-lookup"><span data-stu-id="28578-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="28578-111">未實作。</span><span class="sxs-lookup"><span data-stu-id="28578-111">Not implemented.</span></span> <span data-ttu-id="28578-112">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="28578-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="28578-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="28578-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="28578-114">取得受參考物件目前的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="28578-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="28578-115">IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="28578-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="28578-116">取得值，指出這是否 `ICorDebugReferenceValue` 為 null 值，在此情況下， `ICorDebugReferenceValue` 不會指向物件。</span><span class="sxs-lookup"><span data-stu-id="28578-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="28578-117">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="28578-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="28578-118">設定目前的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="28578-118">Sets the current memory address.</span></span> <span data-ttu-id="28578-119">也就是說，這個方法會將此設定 `ICorDebugReferenceValue` 為指向物件。</span><span class="sxs-lookup"><span data-stu-id="28578-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28578-120">備註</span><span class="sxs-lookup"><span data-stu-id="28578-120">Remarks</span></span>  
 <span data-ttu-id="28578-121">通用語言執行平臺（CLR）可能會在已調試的進程繼續時，對物件進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="28578-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="28578-122">垃圾收集可能會在記憶體中移動物件。</span><span class="sxs-lookup"><span data-stu-id="28578-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="28578-123">`ICorDebugReferenceValue`會與垃圾收集合作，以便在垃圾收集之後更新其資訊，或在垃圾收集之前隱含地將其視為無效。</span><span class="sxs-lookup"><span data-stu-id="28578-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="28578-124">`ICorDebugReferenceValue`繼續進行已調試的進程之後，可能會隱含地使物件失效。</span><span class="sxs-lookup"><span data-stu-id="28578-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="28578-125">衍生的 "ICorDebugHandleValue" 在明確釋放或公開之前不會無效。</span><span class="sxs-lookup"><span data-stu-id="28578-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28578-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="28578-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28578-127">需求</span><span class="sxs-lookup"><span data-stu-id="28578-127">Requirements</span></span>  
 <span data-ttu-id="28578-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28578-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28578-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28578-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28578-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28578-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28578-131">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28578-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28578-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="28578-132">See also</span></span>

- [<span data-ttu-id="28578-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="28578-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
