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
ms.openlocfilehash: 31ecea4857dabc55e8acd3c22a025895a686efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931083"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="e0bc8-102">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="e0bc8-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="e0bc8-103">擴充 ICorDebugProcess 介面以支援存取 managed 堆積, 以提供有關受管理物件之垃圾收集的資訊, 以及判斷偵錯工具是否從應用程式本機原生映射快取載入影像。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0bc8-104">方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-104">Methods</span></span>  
  
|<span data-ttu-id="e0bc8-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-105">Method</span></span>|<span data-ttu-id="e0bc8-106">描述</span><span class="sxs-lookup"><span data-stu-id="e0bc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0bc8-107">EnableNGenPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="e0bc8-108">設定值, 決定應用程式在 managed 偵錯工具下執行時, 載入原生影像的方式。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="e0bc8-109">EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="e0bc8-110">取得要在進程中進行垃圾收集之所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="e0bc8-111">EnumerateHandles 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="e0bc8-112">取得進程中物件控制碼的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="e0bc8-113">EnumerateHeap 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="e0bc8-114">取得 managed 堆積上物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="e0bc8-115">EnumerateHeapRegions 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="e0bc8-116">取得受控堆積區域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="e0bc8-117">GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="e0bc8-118">取得記憶體中陣列版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="e0bc8-119">GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="e0bc8-120">取得[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)結構的指標, 其中包含要在 managed 堆積上進行垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="e0bc8-121">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="e0bc8-122">取得 managed 堆積上物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="e0bc8-123">GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="e0bc8-124">取得陣列的指標, 其中包含根據類型識別碼之類型的欄位資訊。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="e0bc8-125">GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="e0bc8-126">取得型別物件, 根據物件的型別識別碼提供物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="e0bc8-127">GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="e0bc8-128">取得位於指定位址之物件的類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="e0bc8-129">GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e0bc8-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="e0bc8-130">根據物件的類型識別碼, 取得記憶體中之配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0bc8-131">備註</span><span class="sxs-lookup"><span data-stu-id="e0bc8-131">Remarks</span></span>  
 <span data-ttu-id="e0bc8-132">這個介面會以邏輯方式擴充 ICorDebugProcess、ICorDebugProcess2 和[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0bc8-133">此介面不支援從其他電腦或從其他進程遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bc8-134">需求</span><span class="sxs-lookup"><span data-stu-id="e0bc8-134">Requirements</span></span>  
 <span data-ttu-id="e0bc8-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0bc8-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0bc8-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0bc8-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0bc8-137">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0bc8-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0bc8-138">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0bc8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bc8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0bc8-139">See also</span></span>

- [<span data-ttu-id="e0bc8-140">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0bc8-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e0bc8-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="e0bc8-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
