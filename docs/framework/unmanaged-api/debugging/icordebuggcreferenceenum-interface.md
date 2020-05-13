---
title: ICorDebugGCReferenceEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213097"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="a9228-102">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a9228-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="a9228-103">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="a9228-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9228-104">方法</span><span class="sxs-lookup"><span data-stu-id="a9228-104">Methods</span></span>  
  
|<span data-ttu-id="a9228-105">方法</span><span class="sxs-lookup"><span data-stu-id="a9228-105">Method</span></span>|<span data-ttu-id="a9228-106">描述</span><span class="sxs-lookup"><span data-stu-id="a9228-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9228-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="a9228-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="a9228-108">取得指定的[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9228-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9228-109">備註</span><span class="sxs-lookup"><span data-stu-id="a9228-109">Remarks</span></span>  
 <span data-ttu-id="a9228-110">介面會執行 `ICorDebugGCReferenceEnum` "ICorDebugEnum" 介面。</span><span class="sxs-lookup"><span data-stu-id="a9228-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="a9228-111">`ICorDebugGCReferenceEnum`實例會藉由呼叫[ICorDebugProcess5：： EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md)方法來填入[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="a9228-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="a9228-112">藉由呼叫[ICorDebugGCReference：： Next](icordebuggcreferenceenum-next-method.md)方法，可以列舉[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a9228-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="a9228-113">這個方法所填入之集合中的[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件代表三種物件：</span><span class="sxs-lookup"><span data-stu-id="a9228-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="a9228-114">來自所有 managed 堆疊的物件。</span><span class="sxs-lookup"><span data-stu-id="a9228-114">Objects from all managed stacks.</span></span> <span data-ttu-id="a9228-115">這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="a9228-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="a9228-116">控制碼資料表中的物件。</span><span class="sxs-lookup"><span data-stu-id="a9228-116">Objects from the handle table.</span></span> <span data-ttu-id="a9228-117">這包括強式參考（ `HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT` ），以及模組中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="a9228-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="a9228-118">完成項佇列中的物件。</span><span class="sxs-lookup"><span data-stu-id="a9228-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="a9228-119">完成項會佇列根物件，直到完成項執行為止。</span><span class="sxs-lookup"><span data-stu-id="a9228-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9228-120">需求</span><span class="sxs-lookup"><span data-stu-id="a9228-120">Requirements</span></span>  
 <span data-ttu-id="a9228-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9228-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9228-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9228-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9228-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9228-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9228-124">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9228-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9228-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9228-125">See also</span></span>

- [<span data-ttu-id="a9228-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a9228-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
