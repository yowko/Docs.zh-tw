---
title: 偵錯介面
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981604"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="68735-102">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="68735-102">Debugging Interfaces</span></span>
<span data-ttu-id="68735-103">本節說明 Unmanaged 介面，這類介面會處理通用語言執行平台 (CLR) 中所執行之程式的偵錯。</span><span class="sxs-lookup"><span data-stu-id="68735-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68735-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="68735-104">In This Section</span></span>  
 <span data-ttu-id="68735-105">[ICLRDataEnumMemoryRegions 介面](iclrdataenummemoryregions-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\\</span></span>
 <span data-ttu-id="68735-106">提供方法來列舉呼叫端所指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="68735-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="68735-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span></span>
 <span data-ttu-id="68735-108">提供回呼方法，讓 `EnumMemoryRegions` 向偵錯工具報告嘗試列舉指定之記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="68735-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="68735-109">[ICLRDataTarget 介面](iclrdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="68735-110">提供方法與目標 CLR 處理序互動。</span><span class="sxs-lookup"><span data-stu-id="68735-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="68735-111">[ICLRDataTarget2 介面](iclrdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="68735-112">
  `ICLRDataTarget\` 的子類別，資料存取服務層會使用它來管理目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="68735-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="68735-113">[ICLRDataTarget3 介面](iclrdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="68735-114">子類別[ICLRDataTarget2](iclrdatatarget2-interface.md)提供例外狀況資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="68735-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="68735-115">[ICLRDebugging 介面](iclrdebugging-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\\</span></span>
 <span data-ttu-id="68735-116">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="68735-117">[ICLRDebuggingLibraryProvider 介面](iclrdebugginglibraryprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\\</span></span>
 <span data-ttu-id="68735-118">包含[ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md)方法，以取得程式庫提供者回呼介面，可讓通用語言執行階段版本特定偵錯程式庫尋找並載入需求。</span><span class="sxs-lookup"><span data-stu-id="68735-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="68735-119">[ICLRMetadataLocator 介面](iclrmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="68735-120">由資料存取服務層用來尋找目標處理序中之組件中繼資料的介面。</span><span class="sxs-lookup"><span data-stu-id="68735-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="68735-121">[ICorDebug 介面](icordebug-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-121">[ICorDebug Interface](icordebug-interface.md)\\</span></span>
 <span data-ttu-id="68735-122">提供方法讓開發人員於 CLR 環境中為應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="68735-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="68735-123">[ICorDebugAppDomain 介面](icordebugappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\\</span></span>
 <span data-ttu-id="68735-124">提供偵錯應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="68735-125">[ICorDebugAppDomain2 介面](icordebugappdomain2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\\</span></span>
 <span data-ttu-id="68735-126">提供方法來使用陣列、指標、函式指標和 ByRef 類型。</span><span class="sxs-lookup"><span data-stu-id="68735-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="68735-127">這個介面是 `ICorDebugAppDomain` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="68735-128">[ICorDebugAppDomain3 介面](icordebugappdomain3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span></span>
 <span data-ttu-id="68735-129">提供在應用程式定義域中使用 [!INCLUDE[wrt](../../../../includes/wrt-md.md)]類型的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="68735-130">這個介面是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="68735-131">[ICorDebugAppDomain4 介面](icordebugappdomain4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span></span>
 <span data-ttu-id="68735-132">以邏輯方式擴充[ICorDebugAppDomain](icordebugappdomain-interface.md)從 COM 可呼叫包裝函式取得 managed 的物件的介面。</span><span class="sxs-lookup"><span data-stu-id="68735-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="68735-133">[ICorDebugAppDomainEnum 介面](icordebugappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-134">提供方法，此方法會傳回指定數目的 `ICorDebugAppDomain` 值 (從列舉類型中的下一個位置開始)。</span><span class="sxs-lookup"><span data-stu-id="68735-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="68735-135">[ICorDebugArrayValue 介面](icordebugarrayvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-136">表示一維或多維陣列之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="68735-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="68735-137">[ICorDebugAssembly 介面](icordebugassembly-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)\\</span></span>
 <span data-ttu-id="68735-138">表示組件。</span><span class="sxs-lookup"><span data-stu-id="68735-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="68735-139">[ICorDebugAssembly2 介面](icordebugassembly2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\\</span></span>
 <span data-ttu-id="68735-140">表示組件。</span><span class="sxs-lookup"><span data-stu-id="68735-140">Represents an assembly.</span></span> <span data-ttu-id="68735-141">這個介面是 `ICorDebugAssembly` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="68735-142">[ICorDebugAssembly3 介面](icordebugassembly3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\\</span></span>
 <span data-ttu-id="68735-143">以邏輯方式擴充[ICorDebugAssembly](icordebugassembly-interface.md)介面，以提供支援給容器組件及其所包含的組件。</span><span class="sxs-lookup"><span data-stu-id="68735-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="68735-144">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-145">[ICorDebugAssemblyEnum 介面](icordebugassemblyenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-146">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugAssembly` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="68735-147">[ICorDebugBlockingObjectEnum 介面](icordebugblockingobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-148">提供列舉值，取得一份[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="68735-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="68735-149">[ICorDebugBoxValue 介面](icordebugboxvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-150">
  `ICorDebugHeapValue\` 的子類別，表示 Boxed 值的類別物件。</span><span class="sxs-lookup"><span data-stu-id="68735-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="68735-151">[ICorDebugBreakpoint 介面](icordebugbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="68735-152">表示函式中的中斷點，或是某個值上的監看點。</span><span class="sxs-lookup"><span data-stu-id="68735-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="68735-153">[ICorDebugBreakpointEnum 介面](icordebugbreakpointenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-154">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugBreakpoint` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="68735-155">[ICorDebugChain 介面](icordebugchain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-155">[ICorDebugChain Interface](icordebugchain-interface.md)\\</span></span>
 <span data-ttu-id="68735-156">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="68735-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="68735-157">[ICorDebugChainEnum 介面](icordebugchainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-158">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugChain` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="68735-159">[ICorDebugClass 介面](icordebugclass-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-159">[ICorDebugClass Interface](icordebugclass-interface.md)\\</span></span>
 <span data-ttu-id="68735-160">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="68735-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="68735-161">如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="68735-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="68735-162">[ICorDebugClass2 介面](icordebugclass2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\\</span></span>
 <span data-ttu-id="68735-163">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="68735-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="68735-164">這個介面延伸 `ICorDebugClass`。</span><span class="sxs-lookup"><span data-stu-id="68735-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="68735-165">[ICorDebugCode 介面](icordebugcode-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-165">[ICorDebugCode Interface](icordebugcode-interface1.md)\\</span></span>
 <span data-ttu-id="68735-166">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="68735-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="68735-167">[ICorDebugCode2 介面](icordebugcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)\\</span></span>
 <span data-ttu-id="68735-168">提供方法來擴充 `ICorDebugCode` 的功能。</span><span class="sxs-lookup"><span data-stu-id="68735-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="68735-169">[ICorDebugCode3 介面](icordebugcode3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\\</span></span>
 <span data-ttu-id="68735-170">提供擴充方法[ICorDebugCode](icordebugcode-interface1.md)並[ICorDebugCode2](icordebugcode2-interface.md)提供 managed 傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="68735-171">[ICorDebugCode4 介面](icordebugcode4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\\</span></span>
 <span data-ttu-id="68735-172">提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="68735-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="68735-173">[ICorDebugCodeEnum 介面](icordebugcodeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-174">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugCode` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="68735-175">[ICorDebugComObjectValue 介面](icordebugcomobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-176">提供擷取快取介面物件的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="68735-177">[ICorDebugContext 介面](icordebugcontext-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\\</span></span>
 <span data-ttu-id="68735-178">表示內容物件。</span><span class="sxs-lookup"><span data-stu-id="68735-178">Represents a context object.</span></span> <span data-ttu-id="68735-179">尚未實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="68735-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="68735-180">[ICorDebugController 介面](icordebugcontroller-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\\</span></span>
 <span data-ttu-id="68735-181">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="68735-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="68735-182">[ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="68735-183">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="68735-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="68735-184">[ICorDebugDataTarget2 介面](icordebugdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="68735-185">以邏輯方式擴充[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="68735-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="68735-186">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-187">[ICorDebugDataTarget3 介面](icordebugdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="68735-188">以邏輯方式擴充[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面，以提供已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="68735-189">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-190">[ICorDebugDebugEvent 介面](icordebugdebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\\</span></span>
 <span data-ttu-id="68735-191">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="68735-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="68735-192">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-193">[ICorDebugEditAndContinueErrorInfo 介面](icordebugeditandcontinueerrorinfo-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span></span>
 <span data-ttu-id="68735-194">已過時。</span><span class="sxs-lookup"><span data-stu-id="68735-194">Obsolete.</span></span> <span data-ttu-id="68735-195">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="68735-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="68735-196">[ICorDebugEditAndContinueSnapshot 介面](icordebugeditandcontinuesnapshot-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\\</span></span>
 <span data-ttu-id="68735-197">已過時。</span><span class="sxs-lookup"><span data-stu-id="68735-197">Obsolete.</span></span> <span data-ttu-id="68735-198">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="68735-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="68735-199">[ICorDebugEnum 介面](icordebugenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)\\</span></span>
 <span data-ttu-id="68735-200">當做抽象基底介面來偵錯列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="68735-201">[ICorDebugErrorInfoEnum 介面](icordebugerrorinfoenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-202">已過時。</span><span class="sxs-lookup"><span data-stu-id="68735-202">Obsolete.</span></span> <span data-ttu-id="68735-203">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="68735-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="68735-204">[ICorDebugEval 介面](icordebugeval-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-204">[ICorDebugEval Interface](icordebugeval-interface.md)\\</span></span>
 <span data-ttu-id="68735-205">提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="68735-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="68735-206">[ICorDebugEval2 介面](icordebugeval2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)\\</span></span>
 <span data-ttu-id="68735-207">擴充 `ICorDebugEval` 來提供泛型類型的支援。</span><span class="sxs-lookup"><span data-stu-id="68735-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="68735-208">[ICorDebugExceptionDebugEvent 介面](icordebugexceptiondebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\\</span></span>
 <span data-ttu-id="68735-209">擴充[ICorDebugDebugEvent](icordebugdebugevent-interface.md)介面，以支援例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="68735-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="68735-210">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-211">[ICorDebugExceptionObjectCallStackEnum 介面](icordebugexceptionobjectcallstackenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-212">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="68735-213">[ICorDebugExceptionObjectValue 介面](icordebugexceptionobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-214">擴充[ICorDebugObjectValue](icordebugobjectvalue-interface.md)介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="68735-215">[ICorDebugFrame 介面](icordebugframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\\</span></span>
 <span data-ttu-id="68735-216">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="68735-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="68735-217">[ICorDebugFrameEnum 介面](icordebugframeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-218">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugFrame` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="68735-219">[ICorDebugFunction 介面](icordebugfunction-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)\\</span></span>
 <span data-ttu-id="68735-220">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="68735-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="68735-221">[ICorDebugFunction2 介面](icordebugfunction2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\\</span></span>
 <span data-ttu-id="68735-222">以邏輯方式擴充 `ICorDebugFunction`，為 Just My Code 逐步執行的偵錯提供支援。</span><span class="sxs-lookup"><span data-stu-id="68735-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="68735-223">[ICorDebugFunction3 介面](icordebugfunction3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\\</span></span>
 <span data-ttu-id="68735-224">以邏輯方式擴充[ICorDebugFunction](icordebugfunction-interface1.md)介面，以從 ReJIT 要求提供存取權的程式碼。</span><span class="sxs-lookup"><span data-stu-id="68735-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="68735-225">[ICorDebugFunctionBreakpoint 介面](icordebugfunctionbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="68735-226">擴充 `ICorDebugBreakpoint` 來支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="68735-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="68735-227">[ICorDebugGCReferenceEnum 介面](icordebuggcreferenceenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-228">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="68735-229">[ICorDebugGenericValue 介面](icordebuggenericvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-230">套用至所有值之 `ICorDebugValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="68735-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="68735-231">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="68735-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="68735-232">[ICorDebugGuidToTypeEnum 介面](icordebugguidtotypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-233">為對應 GUID 和其相應 `ICorDebugType` 物件的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="68735-234">[ICorDebugHandleValue 介面](icordebughandlevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-235">
  `ICorDebugReferenceValue\` 的子類別，表示偵錯工具已建立記憶體回收控制代碼的參考值。</span><span class="sxs-lookup"><span data-stu-id="68735-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="68735-236">[ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-237">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="68735-238">[ICorDebugHeapSegmentEnum 介面](icordebugheapsegmentenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-239">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="68735-240">[ICorDebugHeapValue 介面](icordebugheapvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-241">
  `ICorDebugValue\` 的子類別，表示 CLR 記憶體回收行程所回收的物件。</span><span class="sxs-lookup"><span data-stu-id="68735-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="68735-242">[ICorDebugHeapValue2 介面](icordebugheapvalue2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\\</span></span>
 <span data-ttu-id="68735-243">
  `ICorDebugHeapValue\` 的擴充，其支援執行階段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="68735-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="68735-244">[ICorDebugHeapValue3 介面](icordebugheapvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\\</span></span>
 <span data-ttu-id="68735-245">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="68735-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="68735-246">[ICorDebugILCode 介面](icordebugilcode-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\\</span></span>
 <span data-ttu-id="68735-247">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="68735-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="68735-248">[ICorDebugILCode2 介面](icordebugilcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\\</span></span>
 <span data-ttu-id="68735-249">以邏輯方式擴充[ICorDebugILCode](icordebugilcode-interface.md)介面，以提供的方法，傳回的語彙基元函式的區域變數簽章，而且，它將對應的分析工具檢測中繼語言 (IL) 位移到原始方法 IL位移。</span><span class="sxs-lookup"><span data-stu-id="68735-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="68735-250">[ICorDebugILFrame 介面](icordebugilframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\\</span></span>
 <span data-ttu-id="68735-251">表示 MSIL 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="68735-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="68735-252">[ICorDebugILFrame2 介面](icordebugilframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\\</span></span>
 <span data-ttu-id="68735-253">
  `ICorDebugILFrame\` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="68735-254">[ICorDebugILFrame3 介面](icordebugilframe3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\\</span></span>
 <span data-ttu-id="68735-255">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="68735-256">[ICorDebugILFrame4 介面](icordebugilframe4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\\</span></span>
 <span data-ttu-id="68735-257">提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="68735-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="68735-258">參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="68735-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="68735-259">[ICorDebugInstanceFieldSymbol 介面](icordebuginstancefieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="68735-260">代表執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="68735-261">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-262">[ICorDebugInternalFrame 介面](icordebuginternalframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\\</span></span>
 <span data-ttu-id="68735-263">識別偵錯工具的框架類型。</span><span class="sxs-lookup"><span data-stu-id="68735-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="68735-264">[ICorDebugInternalFrame2 介面](icordebuginternalframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\\</span></span>
 <span data-ttu-id="68735-265">提供內部框架，包括堆疊位址和位置的相關資訊[ICorDebugFrame](icordebugframe-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="68735-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="68735-266">[ICorDebugLoadedModule 介面](icordebugloadedmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\\</span></span>
 <span data-ttu-id="68735-267">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-267">Provides information about a loaded module.</span></span> <span data-ttu-id="68735-268">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="68735-270">提供方法來處理偵錯工具回呼。</span><span class="sxs-lookup"><span data-stu-id="68735-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="68735-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span></span>
 <span data-ttu-id="68735-272">提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="68735-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="68735-273">`ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="68735-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span></span>
 <span data-ttu-id="68735-275">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="68735-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="68735-276">[ICorDebugMDA 介面](icordebugmda-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\\</span></span>
 <span data-ttu-id="68735-277">表示 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="68735-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="68735-278">[ICorDebugMemoryBuffer 介面](icordebugmemorybuffer-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\\</span></span>
 <span data-ttu-id="68735-279">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="68735-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="68735-280">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-281">[ICorDebugMergedAssemblyRecord 介面](icordebugmergedassemblyrecord-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\\</span></span>
 <span data-ttu-id="68735-282">提供合併組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="68735-283">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-284">[ICorDebugMetaDataLocator 介面](icordebugmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="68735-285">提供中繼資料資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="68735-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="68735-286">[ICorDebugModule 介面](icordebugmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\\</span></span>
 <span data-ttu-id="68735-287">表示 CLR 模組，其為可執行檔或動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="68735-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="68735-288">[ICorDebugModule2 介面](icordebugmodule2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\\</span></span>
 <span data-ttu-id="68735-289">當做 `ICorDebugModule` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="68735-290">[ICorDebugModule3 介面](icordebugmodule3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\\</span></span>
 <span data-ttu-id="68735-291">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="68735-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="68735-292">[ICorDebugModuleBreakpoint 介面](icordebugmodulebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="68735-293">擴充 `ICorDebugBreakpoint`，以提供特定模組的存取權。</span><span class="sxs-lookup"><span data-stu-id="68735-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="68735-294">[ICorDebugModuleDebugEvent 介面](icordebugmoduledebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\\</span></span>
 <span data-ttu-id="68735-295">擴充[ICorDebugDebugEvent](icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="68735-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="68735-296">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-297">[ICorDebugModuleEnum 介面](icordebugmoduleenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-298">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugModule` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="68735-299">[ICorDebugMutableDataTarget 介面](icordebugmutabledatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span></span>
 <span data-ttu-id="68735-300">擴充[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面，以支援可變動的資料目標。</span><span class="sxs-lookup"><span data-stu-id="68735-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="68735-301">[ICorDebugNativeFrame 介面](icordebugnativeframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\\</span></span>
 <span data-ttu-id="68735-302">用於原生框架的 `ICorDebugFrame` 特定實作。</span><span class="sxs-lookup"><span data-stu-id="68735-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="68735-303">[ICorDebugNativeFrame2 介面](icordebugnativeframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\\</span></span>
 <span data-ttu-id="68735-304">提供測試父子框架關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="68735-305">[ICorDebugObjectEnum 介面](icordebugobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-306">實作 `ICorDebugEnum` 方法，並根據物件陣列的相對虛擬位址 (RVA) 來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="68735-307">[ICorDebugObjectValue 介面](icordebugobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-308">
  `ICorDebugValue\` 的子類別，表示包含物件的值。</span><span class="sxs-lookup"><span data-stu-id="68735-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="68735-309">[ICorDebugObjectValue2 介面](icordebugobjectvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\\</span></span>
 <span data-ttu-id="68735-310">擴充 `ICorDebugObjectValue` 來支援繼承和覆寫。</span><span class="sxs-lookup"><span data-stu-id="68735-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="68735-311">[ICorDebugProcess 介面](icordebugprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)\\</span></span>
 <span data-ttu-id="68735-312">表示執行 Managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="68735-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="68735-313">[ICorDebugProcess2 介面](icordebugprocess2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\\</span></span>
 <span data-ttu-id="68735-314">
  `ICorDebugProcess\` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="68735-315">[ICorDebugProcess3 介面](icordebugprocess3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\\</span></span>
 <span data-ttu-id="68735-316">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="68735-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="68735-317">[ICorDebugProcess4 介面](icordebugprocess4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\\</span></span>
 <span data-ttu-id="68735-318">提供支援失控程序執行。</span><span class="sxs-lookup"><span data-stu-id="68735-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="68735-319">[ICorDebugProcess5 介面](icordebugprocess5-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\\</span></span>
 <span data-ttu-id="68735-320">擴充[ICorDebugProcess](icordebugprocess-interface.md)介面，以支援存取 managed 堆積，以提供受管理的物件，記憶體回收的相關資訊，以及判斷偵錯工具是否從應用程式載入影像的本機原生映像快取。</span><span class="sxs-lookup"><span data-stu-id="68735-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="68735-321">[ICorDebugProcess6 介面](icordebugprocess6-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\\</span></span>
 <span data-ttu-id="68735-322">以邏輯方式擴充[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用功能，例如解碼的編碼原生例外狀況偵錯事件，以及虛擬模組分割的 managed 偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="68735-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="68735-323">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-324">[ICorDebugProcess7 介面](icordebugprocess7-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\\</span></span>
 <span data-ttu-id="68735-325">提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。</span><span class="sxs-lookup"><span data-stu-id="68735-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="68735-326">[ICorDebugProcess8 介面](icordebugprocess8-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\\</span></span>
 <span data-ttu-id="68735-327">以邏輯方式擴充[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用或停用特定類型的[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="68735-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="68735-328">[ICorDebugProcessEnum 介面](icordebugprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-329">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugProcess` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="68735-330">[ICorDebugReferenceValue 介面](icordebugreferencevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-331">支援參考類型的 `ICorDebugValue` 子類別。</span><span class="sxs-lookup"><span data-stu-id="68735-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="68735-332">[ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\\</span></span>
 <span data-ttu-id="68735-333">表示目前在機器上執行程式碼的可用暫存器集合。</span><span class="sxs-lookup"><span data-stu-id="68735-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="68735-334">[ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\\</span></span>
 <span data-ttu-id="68735-335">為具有 64 個以上暫存器的硬體平台，擴充 `ICorDebugRegisterSet` 的功能。</span><span class="sxs-lookup"><span data-stu-id="68735-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="68735-336">[ICorDebugRemote 介面](icordebugremote-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\\</span></span>
 <span data-ttu-id="68735-337">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="68735-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="68735-338">[ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\\</span></span>
 <span data-ttu-id="68735-339">提供可讓您對 CLR 環境中的 Silverlight 應用程式進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="68735-340">[ICorDebugRuntimeUnwindableFrame 介面](icordebugruntimeunwindableframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span></span>
 <span data-ttu-id="68735-341">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="68735-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="68735-342">[ICorDebugStackWalk 介面](icordebugstackwalk-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\\</span></span>
 <span data-ttu-id="68735-343">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="68735-344">[ICorDebugStaticFieldSymbol 介面](icordebugstaticfieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="68735-345">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="68735-346">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-347">[ICorDebugStepper 介面](icordebugstepper-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)\\</span></span>
 <span data-ttu-id="68735-348">表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。</span><span class="sxs-lookup"><span data-stu-id="68735-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="68735-349">[ICorDebugStepper2 介面](icordebugstepper2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\\</span></span>
 <span data-ttu-id="68735-350">提供 Just My Code (JMC) 偵錯的支援。</span><span class="sxs-lookup"><span data-stu-id="68735-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="68735-351">[ICorDebugStepperEnum 介面](icordebugstepperenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-352">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugStepper` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="68735-353">[ICorDebugStringValue 介面](icordebugstringvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-354">套用至字串值之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="68735-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="68735-355">[ICorDebugSymbolProvider 介面](icordebugsymbolprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\\</span></span>
 <span data-ttu-id="68735-356">提供可用來擷取偵錯符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="68735-357">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-358">[ICorDebugSymbolProvider2 介面](icordebugsymbolprovider2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\\</span></span>
 <span data-ttu-id="68735-359">以邏輯方式擴充[ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)來擷取其他偵錯符號資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="68735-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="68735-360">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-361">[ICorDebugThread 介面](icordebugthread-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-361">[ICorDebugThread Interface](icordebugthread-interface.md)\\</span></span>
 <span data-ttu-id="68735-362">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="68735-362">Represents a thread in a process.</span></span> <span data-ttu-id="68735-363">
  `ICorDebugThread\` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="68735-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="68735-364">[ICorDebugThread2 介面](icordebugthread2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)\\</span></span>
 <span data-ttu-id="68735-365">當做 `ICorDebugThread` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="68735-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="68735-366">[ICorDebugThread3 介面](icordebugthread3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\\</span></span>
 <span data-ttu-id="68735-367">提供的進入點[ICorDebugStackWalk](icordebugstackwalk-interface.md)和對應的介面。</span><span class="sxs-lookup"><span data-stu-id="68735-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="68735-368">[ICorDebugThread4 介面](icordebugthread4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\\</span></span>
 <span data-ttu-id="68735-369">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="68735-370">[ICorDebugThreadEnum 介面](icordebugthreadenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\\</span></span>
 <span data-ttu-id="68735-371">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugThread` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="68735-372">[ICorDebugType 介面](icordebugtype-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-372">[ICorDebugType Interface](icordebugtype-interface.md)\\</span></span>
 <span data-ttu-id="68735-373">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="68735-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="68735-374">如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="68735-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="68735-375">[ICorDebugType2 介面](icordebugtype2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\\</span></span>
 <span data-ttu-id="68735-376">擴充[ICorDebugType](icordebugtype-interface.md)介面來擷取基底型別或複雜的 （使用者定義） 型別的型別識別項。</span><span class="sxs-lookup"><span data-stu-id="68735-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="68735-377">[ICorDebugTypeEnum 介面](icordebugtypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-378">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugType` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="68735-379">[ICorDebugUnmanagedCallback 介面](icordebugunmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="68735-380">提供未直接與 CLR 有關之原生事件的告知。</span><span class="sxs-lookup"><span data-stu-id="68735-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="68735-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span></span>
 <span data-ttu-id="68735-382">表示所偵錯之處理序中的讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="68735-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="68735-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span></span>
 <span data-ttu-id="68735-384">擴充 `ICorDebugValue` 來提供 `ICorDebugType` 的支援。</span><span class="sxs-lookup"><span data-stu-id="68735-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="68735-385">[ICorDebugValue3 介面](icordebugvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\\</span></span>
 <span data-ttu-id="68735-386">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="68735-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="68735-388">擴充 `ICorDebugBreakpoint`，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="68735-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="68735-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-390">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugValue` 陣列。</span><span class="sxs-lookup"><span data-stu-id="68735-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="68735-391">[ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\\</span></span>
 <span data-ttu-id="68735-392">代表本機變數或函式的引數。</span><span class="sxs-lookup"><span data-stu-id="68735-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="68735-393">[ICorDebugVariableHomeEnum 介面](icordebugvariablehomeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-394">提供的本機變數和引數的函式中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="68735-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="68735-395">[ICorDebugVariableSymbol 介面](icordebugvariablesymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\\</span></span>
 <span data-ttu-id="68735-396">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="68735-397">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-398">[ICorDebugVirtualUnwinder 介面](icordebugvirtualunwinder-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\\</span></span>
 <span data-ttu-id="68735-399">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="68735-400">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="68735-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="68735-401">[ICorPublish 介面](icorpublish-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-401">[ICorPublish Interface](icorpublish-interface.md)\\</span></span>
 <span data-ttu-id="68735-402">當做發行處理序的一般介面。</span><span class="sxs-lookup"><span data-stu-id="68735-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="68735-403">[ICorPublishAppDomain 介面](icorpublishappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\\</span></span>
 <span data-ttu-id="68735-404">表示及提供與應用程式定義域有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="68735-405">[ICorPublishAppDomainEnum 介面](icorpublishappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-406">提供方法來周遊目前存在於處理序中之 `ICorPublishAppDomain` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="68735-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="68735-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-408">當做發行列舉值的抽象基底。</span><span class="sxs-lookup"><span data-stu-id="68735-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="68735-409">[ICorPublishProcess 介面](icorpublishprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\\</span></span>
 <span data-ttu-id="68735-410">提供存取處理序相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="68735-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="68735-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="68735-412">提供方法來周遊 `ICorPublishProcess` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="68735-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="68735-413">[ISOSDacInterface 介面](isosdacinterface-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\\</span></span>
 <span data-ttu-id="68735-414">提供 helper 方法來存取資料，從`SOS`。</span><span class="sxs-lookup"><span data-stu-id="68735-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="68735-415">[IXCLRDataMethodDefinition 介面](ixclrdatamethoddefinition-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\\</span></span>
 <span data-ttu-id="68735-416">提供方法來查詢方法定義的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="68735-417">[IXCLRDataMethodInstance 介面](ixclrdatamethodinstance-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\\</span></span>
 <span data-ttu-id="68735-418">提供方法來查詢的方法執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="68735-419">[IXCLRDataModule 介面](ixclrdatamodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\\</span></span>
 <span data-ttu-id="68735-420">提供方法來查詢載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="68735-421">[IXCLRDataProcess 介面](ixclrdataprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\\</span></span>
 <span data-ttu-id="68735-422">提供方法來查詢處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68735-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="68735-423">相關章節</span><span class="sxs-lookup"><span data-stu-id="68735-423">Related Sections</span></span>  
 <span data-ttu-id="68735-424">[偵錯 Coclass](debugging-coclasses.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-424">[Debugging Coclasses](debugging-coclasses.md)\\</span></span>
 <span data-ttu-id="68735-425">[偵錯全域靜態函式](debugging-global-static-functions.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-425">[Debugging Global Static Functions](debugging-global-static-functions.md)\\</span></span>
 <span data-ttu-id="68735-426">[偵錯列舉](debugging-enumerations.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-426">[Debugging Enumerations](debugging-enumerations.md)\\</span></span>
 <span data-ttu-id="68735-427">[偵錯結構](debugging-structures.md)\\</span><span class="sxs-lookup"><span data-stu-id="68735-427">[Debugging Structures](debugging-structures.md)\\</span></span>
