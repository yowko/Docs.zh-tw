---
title: 偵錯結構
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698355"
---
# <a name="debugging-structures"></a><span data-ttu-id="15c02-102">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="15c02-102">Debugging Structures</span></span>

<span data-ttu-id="15c02-103">本節說明偵錯 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="15c02-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="15c02-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="15c02-104">In This Section</span></span>
 <span data-ttu-id="15c02-105">[CLRDATA_ADDRESS_RANGE 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md)定義的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="15c02-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="15c02-106">[CLRDATA_IL_ADDRESS_MAP 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md)IL 定義位址對應</span><span class="sxs-lookup"><span data-stu-id="15c02-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="15c02-107">[CLR_DEBUGGING_VERSION 結構](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)定義以進行偵錯的 common language runtime (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="15c02-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="15c02-108">[CodeChunkInfo 結構](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)代表單一的記憶體中的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="15c02-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="15c02-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md)包含目前使用中執行緒的框架的函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="15c02-110">[COR_ARRAY_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)提供記憶體中陣列物件配置資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="15c02-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md)包含原生程式碼的程式碼用來對應的 Microsoft intermediate language (MSIL) 位移。</span><span class="sxs-lookup"><span data-stu-id="15c02-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="15c02-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md)包含程式碼範圍的位移的資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="15c02-113">[COR_FIELD 結構](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="15c02-114">[COR_GC_REFERENCE 結構](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="15c02-115">[COR_HEAPINFO 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)提供記憶體回收堆積，包括其是否可列舉的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="15c02-116">[COR_HEAPOBJECT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)managed 堆積上提供物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="15c02-117">[COR_IL_MAP](cor-il-map-structure.md)函式相關位移中指定的變更。</span><span class="sxs-lookup"><span data-stu-id="15c02-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="15c02-118">[COR_SEGMENT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)包含 managed 堆積中的記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="15c02-119">[COR_TYPEID 結構](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)包含型別識別項。</span><span class="sxs-lookup"><span data-stu-id="15c02-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="15c02-120">[COR_TYPE_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)提供記憶體中物件配置資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="15c02-121">[COR_VERSION](cor-version-structure.md)儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="15c02-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="15c02-122">[CorDebugBlockingObject 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)定義執行緒和執行緒封鎖的原因的原因封鎖的物件。</span><span class="sxs-lookup"><span data-stu-id="15c02-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="15c02-123">[CorDebugEHClause 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)表示給定的中繼語言 (IL) 片段的例外狀況處理 (EH) 子句。</span><span class="sxs-lookup"><span data-stu-id="15c02-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="15c02-124">[CorDebugExceptionObjectStackFrame 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)代表堆疊框架資訊的例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="15c02-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="15c02-125">[CorDebugGuidToTypeMapping 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)Maps[!INCLUDE[wrt](../../../../includes/wrt-md.md)]至其相對應的 GUID [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="15c02-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="15c02-126">[DacpGetModuleAddress 結構](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="15c02-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="15c02-127">[DacpMethodDescData 結構](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md)定義方法的執行階段資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="15c02-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="15c02-128">[DacpModuleData 結構](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md)定義模組的執行階段資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="15c02-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="15c02-129">[DacpReJitData 結構](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md)定義指定的程式碼剖析工具檢測方法的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="15c02-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="15c02-130">[StackTrace_SimpleContext 結構](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)提供的簡單的內容，可用來代替完整`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="15c02-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="15c02-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="15c02-131">Related Sections</span></span>

 [<span data-ttu-id="15c02-132">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="15c02-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="15c02-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="15c02-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="15c02-134">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="15c02-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="15c02-135">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="15c02-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="15c02-136">偵錯</span><span class="sxs-lookup"><span data-stu-id="15c02-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
