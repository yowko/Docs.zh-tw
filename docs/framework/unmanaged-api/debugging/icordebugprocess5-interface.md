---
title: ICorDebugProcess5 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948677"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="65172-102">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="65172-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="65172-103">擴充 ICorDebugProcess 介面，以支援存取 managed 堆積，以提供受管理的物件，記憶體回收的相關資訊，並判斷是否在偵錯工具會在 從應用程式本機的原生映像快取載入映像。</span><span class="sxs-lookup"><span data-stu-id="65172-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65172-104">方法</span><span class="sxs-lookup"><span data-stu-id="65172-104">Methods</span></span>  
  
|<span data-ttu-id="65172-105">方法</span><span class="sxs-lookup"><span data-stu-id="65172-105">Method</span></span>|<span data-ttu-id="65172-106">描述</span><span class="sxs-lookup"><span data-stu-id="65172-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65172-107">EnableNGenPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="65172-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="65172-108">設定值，這個值會決定應用程式載入 managed 偵錯工具下執行時的原生映像的方式。</span><span class="sxs-lookup"><span data-stu-id="65172-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="65172-109">EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="65172-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="65172-110">取得要進行記憶體回收處理序中的所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="65172-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="65172-111">EnumerateHandles 方法</span><span class="sxs-lookup"><span data-stu-id="65172-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="65172-112">取得處理序中物件控制代碼的列舉值。</span><span class="sxs-lookup"><span data-stu-id="65172-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="65172-113">EnumerateHeap 方法</span><span class="sxs-lookup"><span data-stu-id="65172-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="65172-114">取得 managed 堆積上物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="65172-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="65172-115">EnumerateHeapRegions 方法</span><span class="sxs-lookup"><span data-stu-id="65172-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="65172-116">取得 managed 堆積的區域中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="65172-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="65172-117">GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="65172-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="65172-118">取得相關資訊的版面配置陣列的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="65172-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="65172-119">GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="65172-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="65172-120">取得指標[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)結構，其中包含要進行記憶體回收 managed 堆積上物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="65172-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="65172-121">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="65172-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="65172-122">取得 managed 堆積上物件的指標。</span><span class="sxs-lookup"><span data-stu-id="65172-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="65172-123">GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="65172-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="65172-124">取得陣列，其中包含根據其型別識別項類型的欄位資訊的指標。</span><span class="sxs-lookup"><span data-stu-id="65172-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="65172-125">GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="65172-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="65172-126">取得型別物件，提供其型別識別項為基礎之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="65172-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="65172-127">GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="65172-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="65172-128">取得物件的型別識別項，在指定的位址。</span><span class="sxs-lookup"><span data-stu-id="65172-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="65172-129">GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="65172-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="65172-130">取得根據其型別識別項的記憶體中的物件配置資訊。</span><span class="sxs-lookup"><span data-stu-id="65172-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65172-131">備註</span><span class="sxs-lookup"><span data-stu-id="65172-131">Remarks</span></span>  
 <span data-ttu-id="65172-132">這個介面會以邏輯方式擴充 ICorDebugProcess，ICorDebugProcess2，並[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="65172-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65172-133">此介面不支援從另一部電腦，或是從另一個處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="65172-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65172-134">需求</span><span class="sxs-lookup"><span data-stu-id="65172-134">Requirements</span></span>  
 <span data-ttu-id="65172-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65172-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65172-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65172-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65172-137">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65172-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65172-138">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65172-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65172-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65172-139">See also</span></span>

- [<span data-ttu-id="65172-140">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="65172-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="65172-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="65172-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
