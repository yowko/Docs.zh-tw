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
ms.openlocfilehash: cef69ac7e3572b67dd676ce8408e4210d93accf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717574"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="93593-102">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="93593-102">ICorDebugProcess5 Interface</span></span>

<span data-ttu-id="93593-103">擴充 ICorDebugProcess 介面以支援存取 managed 堆積，以提供 managed 物件的垃圾收集資訊，以及判斷偵錯工具是否從應用程式本機原生映射快取載入影像。</span><span class="sxs-lookup"><span data-stu-id="93593-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93593-104">方法</span><span class="sxs-lookup"><span data-stu-id="93593-104">Methods</span></span>  
  
|<span data-ttu-id="93593-105">方法</span><span class="sxs-lookup"><span data-stu-id="93593-105">Method</span></span>|<span data-ttu-id="93593-106">描述</span><span class="sxs-lookup"><span data-stu-id="93593-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93593-107">EnableNGenPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="93593-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="93593-108">設定值，這個值會決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。</span><span class="sxs-lookup"><span data-stu-id="93593-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="93593-109">EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="93593-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="93593-110">取得要在進程中進行垃圾收集之所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="93593-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="93593-111">EnumerateHandles 方法</span><span class="sxs-lookup"><span data-stu-id="93593-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="93593-112">取得進程中物件控制碼的列舉值。</span><span class="sxs-lookup"><span data-stu-id="93593-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="93593-113">EnumerateHeap 方法</span><span class="sxs-lookup"><span data-stu-id="93593-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="93593-114">取得 managed 堆積上物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="93593-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="93593-115">EnumerateHeapRegions 方法</span><span class="sxs-lookup"><span data-stu-id="93593-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="93593-116">取得 managed 堆積區域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="93593-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="93593-117">GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="93593-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="93593-118">取得記憶體中陣列版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="93593-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="93593-119">GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="93593-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="93593-120">取得 [COR_HEAPINFO](cor-heapinfo-structure.md) 結構的指標，其中包含要在 managed 堆積上進行垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="93593-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="93593-121">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="93593-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="93593-122">取得 managed 堆積上物件的指標。</span><span class="sxs-lookup"><span data-stu-id="93593-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="93593-123">GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="93593-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="93593-124">取得陣列的指標，該陣列包含以其類型識別碼為基礎之類型的欄位資訊。</span><span class="sxs-lookup"><span data-stu-id="93593-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="93593-125">GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="93593-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="93593-126">取得型別物件，它會根據物件的型別識別碼來提供物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="93593-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="93593-127">GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="93593-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="93593-128">取得位於指定位址之物件的類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="93593-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="93593-129">GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="93593-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="93593-130">根據物件的類型識別碼，取得記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="93593-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93593-131">備註</span><span class="sxs-lookup"><span data-stu-id="93593-131">Remarks</span></span>  

 <span data-ttu-id="93593-132">這個介面會以邏輯方式擴充 ICorDebugProcess、ICorDebugProcess2 和 [ICorDebugProcess3](icordebugprocess3-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="93593-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93593-133">此介面不支援從另一部電腦或另一個進程，從遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="93593-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93593-134">需求</span><span class="sxs-lookup"><span data-stu-id="93593-134">Requirements</span></span>  

 <span data-ttu-id="93593-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93593-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93593-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93593-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93593-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93593-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93593-138">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93593-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93593-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93593-139">See also</span></span>

- [<span data-ttu-id="93593-140">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="93593-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="93593-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="93593-141">Debugging</span></span>](index.md)
