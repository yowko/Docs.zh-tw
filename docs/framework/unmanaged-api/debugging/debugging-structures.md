---
title: "偵錯結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c20bb8a9841b5ebc7a4ca9b5463fe4c541c0a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="80a13-102">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="80a13-102">Debugging Structures</span></span>
<span data-ttu-id="80a13-103">本節說明偵錯 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="80a13-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80a13-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="80a13-104">In This Section</span></span>  
 [<span data-ttu-id="80a13-105">CLR_DEBUGGING_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="80a13-106">定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="80a13-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="80a13-107">CodeChunkInfo 結構 1</span><span class="sxs-lookup"><span data-stu-id="80a13-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="80a13-108">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="80a13-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="80a13-109">CorDebugBlockingObject 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="80a13-110">定義封鎖執行緒的物件，以及封鎖執行緒的原因。</span><span class="sxs-lookup"><span data-stu-id="80a13-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="80a13-111">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="80a13-112">代表給定之中繼語言 (IL) 片段的例外狀況處理 (EH) 子句。</span><span class="sxs-lookup"><span data-stu-id="80a13-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="80a13-113">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="80a13-114">代表例外狀況物件所產生的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="80a13-115">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="80a13-116">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]至其相對應的 GUID [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="80a13-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="80a13-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="80a13-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="80a13-118">包含目前執行緒框架中正在作用的函式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="80a13-119">COR_ARRAY_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="80a13-120">提供記憶體中陣列物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="80a13-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="80a13-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="80a13-122">包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="80a13-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="80a13-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="80a13-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="80a13-124">包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="80a13-125">COR_FIELD 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="80a13-126">提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="80a13-127">COR_GC_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="80a13-128">包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="80a13-129">COR_HEAPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="80a13-130">提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。</span><span class="sxs-lookup"><span data-stu-id="80a13-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="80a13-131">COR_HEAPOBJECT 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="80a13-132">提供 Managed 堆積上的物件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="80a13-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="80a13-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="80a13-134">指定函式相關位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="80a13-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="80a13-135">COR_SEGMENT 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="80a13-136">包含 Managed 堆積中記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="80a13-137">COR_TYPEID 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="80a13-138">包含類型識別項。</span><span class="sxs-lookup"><span data-stu-id="80a13-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="80a13-139">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="80a13-140">提供記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80a13-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="80a13-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="80a13-141">COR_VERSION</span></span>  
 <span data-ttu-id="80a13-142">儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="80a13-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="80a13-143">StackTrace_SimpleContext 結構</span><span class="sxs-lookup"><span data-stu-id="80a13-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="80a13-144">提供可用來代替完整 `CONTEXT` 結構的簡單內容。</span><span class="sxs-lookup"><span data-stu-id="80a13-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80a13-145">相關章節</span><span class="sxs-lookup"><span data-stu-id="80a13-145">Related Sections</span></span>  
 [<span data-ttu-id="80a13-146">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="80a13-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="80a13-147">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="80a13-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="80a13-148">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="80a13-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="80a13-149">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="80a13-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="80a13-150">偵錯</span><span class="sxs-lookup"><span data-stu-id="80a13-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
