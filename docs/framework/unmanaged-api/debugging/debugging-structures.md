---
title: 偵錯結構
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793747"
---
# <a name="debugging-structures"></a><span data-ttu-id="22146-102">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="22146-102">Debugging Structures</span></span>

<span data-ttu-id="22146-103">本節說明偵錯 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="22146-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="22146-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="22146-104">In This Section</span></span>
 <span data-ttu-id="22146-105">[CLRDATA_ADDRESS_RANGE 結構](clrdata-address-range-structure.md)定義位址範圍。</span><span class="sxs-lookup"><span data-stu-id="22146-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="22146-106">[CLRDATA_IL_ADDRESS_MAP 結構](clrdata-il-address-map-structure.md)定義 IL 以定址對應</span><span class="sxs-lookup"><span data-stu-id="22146-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="22146-107">[CLR_DEBUGGING_VERSION 結構](clr-debugging-version-structure.md)定義用於進行偵錯工具之 common language runtime （CLR）的產品版本。</span><span class="sxs-lookup"><span data-stu-id="22146-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="22146-108">[CodeChunkInfo 結構](codechunkinfo-structure.md)代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="22146-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="22146-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md)包含執行緒框架中目前作用中之函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="22146-110">[COR_ARRAY_LAYOUT 結構](cor-array-layout-structure.md)提供記憶體中陣列物件版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="22146-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md)包含用來將 Microsoft 中繼語言（MSIL）程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="22146-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="22146-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md)包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="22146-113">[COR_FIELD 結構](cor-field-structure.md)提供有關物件中欄位的資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="22146-114">[COR_GC_REFERENCE 結構](cor-gc-reference-structure.md)包含要進行垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="22146-115">[COR_HEAPINFO 結構](cor-heapinfo-structure.md)提供有關垃圾收集堆積的一般資訊，包括是否可列舉。</span><span class="sxs-lookup"><span data-stu-id="22146-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="22146-116">[COR_HEAPOBJECT 結構](cor-heapobject-structure.md)提供 managed 堆積上物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="22146-117">[COR_IL_MAP](cor-il-map-structure.md)指定函數的相對位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="22146-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="22146-118">[COR_SEGMENT 結構](cor-segment-structure.md)包含受控堆積中的記憶體區域相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="22146-119">[COR_TYPEID 結構](cor-typeid-structure.md)包含類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="22146-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="22146-120">[COR_TYPE_LAYOUT 結構](cor-type-layout-structure.md)提供記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="22146-121">[COR_VERSION](cor-version-structure.md)儲存 common language runtime 的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="22146-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="22146-122">[CorDebugBlockingObject 結構](cordebugblockingobject-structure.md)定義封鎖執行緒的物件，以及執行緒被封鎖的原因。</span><span class="sxs-lookup"><span data-stu-id="22146-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="22146-123">[CorDebugEHClause 結構](cordebugehclause-structure.md)代表中繼語言（IL）之指定片段的例外狀況處理（EH）子句。</span><span class="sxs-lookup"><span data-stu-id="22146-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="22146-124">[CorDebugExceptionObjectStackFrame 結構](cordebugexceptionobjectstackframe-structure.md)表示來自例外狀況物件的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="22146-125">[CorDebugGuidToTypeMapping 結構](cordebugguidtotypemapping-structure.md)將 Windows 執行階段的 GUID 對應至其相對應的[ICorDebugType](icordebugtype-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="22146-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="22146-126">[DacpGetModuleAddress 結構](dacpgetmoduleaddress-structure.md)定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="22146-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="22146-127">[DacpMethodDescData 結構](dacpmethoddescdata-structure.md)為方法的執行時間資訊定義傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="22146-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="22146-128">[Dacpmethoddata 結構](dacpmoduledata-structure.md)定義模組執行時間資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="22146-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="22146-129">[DacpReJitData 結構](dacprejitdata-structure.md)定義指定之分析工具檢測方法的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="22146-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="22146-130">[StackTrace_SimpleCoNtext 結構](stacktrace-simplecontext-structure.md)提供一個簡單的內容，可用來取代完整的 `CONTEXT` 結構。</span><span class="sxs-lookup"><span data-stu-id="22146-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="22146-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="22146-131">Related Sections</span></span>

 [<span data-ttu-id="22146-132">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="22146-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="22146-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="22146-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="22146-134">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="22146-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="22146-135">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="22146-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="22146-136">偵錯</span><span class="sxs-lookup"><span data-stu-id="22146-136">Debugging</span></span>](index.md)
