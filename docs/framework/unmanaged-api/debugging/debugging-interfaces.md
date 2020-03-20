---
title: 偵錯介面
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179170"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="0c415-102">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0c415-102">Debugging Interfaces</span></span>
<span data-ttu-id="0c415-103">本節說明 Unmanaged 介面，這類介面會處理通用語言執行平台 (CLR) 中所執行之程式的偵錯。</span><span class="sxs-lookup"><span data-stu-id="0c415-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c415-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="0c415-104">In This Section</span></span>  
 <span data-ttu-id="0c415-105">[ICLR 資料記憶區介面](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="0c415-106">提供方法來列舉呼叫端所指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="0c415-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="0c415-107">[ICLRDataEnum記憶體區域回檔介面](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="0c415-108">提供回呼方法，讓 `EnumMemoryRegions` 向偵錯工具報告嘗試列舉指定之記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="0c415-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="0c415-109">[ICLR資料目標介面](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="0c415-110">提供方法與目標 CLR 處理序互動。</span><span class="sxs-lookup"><span data-stu-id="0c415-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="0c415-111">[ICLRDataTarget2 介面](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="0c415-112">`ICLRDataTarget` 的子類別，資料存取服務層會使用它來管理目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="0c415-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="0c415-113">[ICLRDataTarget3 介面](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="0c415-114">[ICLRDataTarget2](iclrdatatarget2-interface.md)的子類，提供對異常資訊的訪問。</span><span class="sxs-lookup"><span data-stu-id="0c415-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="0c415-115">[ICLR調試介面](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="0c415-116">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="0c415-117">[ICLR調試庫提供程式介面](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="0c415-118">包括[ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md)，該方法獲取庫提供程式回檔介面，允許按需定位和載入通用語言運行時特定調試庫。</span><span class="sxs-lookup"><span data-stu-id="0c415-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="0c415-119">[ICLR元形定位器介面](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="0c415-120">由資料存取服務層用來尋找目標處理序中之組件中繼資料的介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="0c415-121">[ICorDebug 介面](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="0c415-122">提供方法讓開發人員於 CLR 環境中為應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="0c415-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="0c415-123">[ICorDebugApp域介面](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="0c415-124">提供偵錯應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="0c415-125">[ICorDebugAppDomain2 介面](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="0c415-126">提供方法來使用陣列、指標、函式指標和 ByRef 類型。</span><span class="sxs-lookup"><span data-stu-id="0c415-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="0c415-127">這個介面是 `ICorDebugAppDomain` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="0c415-128">[ICorDebugAppDomain3 介面](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="0c415-129">提供了用於在應用程式域中處理 Windows 運行時類型的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="0c415-130">這個介面是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="0c415-131">[ICorDebugAppDomain4 介面](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="0c415-132">從邏輯上擴展[ICorDebugAppDomain](icordebugappdomain-interface.md)介面，以便從 COM 可調用包裝器獲取託管物件。</span><span class="sxs-lookup"><span data-stu-id="0c415-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="0c415-133">[ICorDebugAppDomainEnum 介面](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-134">提供方法，此方法會傳回指定數目的 `ICorDebugAppDomain` 值 (從列舉類型中的下一個位置開始)。</span><span class="sxs-lookup"><span data-stu-id="0c415-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="0c415-135">[ICorDebugarray值介面](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-136">表示一維或多維陣列之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="0c415-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="0c415-137">[ICorDebug組裝介面](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="0c415-138">表示組件。</span><span class="sxs-lookup"><span data-stu-id="0c415-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="0c415-139">[ICorDebugAssembly2 介面](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="0c415-140">表示組件。</span><span class="sxs-lookup"><span data-stu-id="0c415-140">Represents an assembly.</span></span> <span data-ttu-id="0c415-141">這個介面是 `ICorDebugAssembly` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="0c415-142">[ICorDebugAssembly3 介面](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="0c415-143">從邏輯上講，擴展[ICorDebugAssembly](icordebugassembly-interface.md)介面，以支援容器程式集及其包含的程式集。</span><span class="sxs-lookup"><span data-stu-id="0c415-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="0c415-144">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-145">[ICorDebug組裝Enum介面](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-146">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugAssembly` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="0c415-147">[ICorDebugBlockingobjectenum 介面](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-148">為[CorDebugBlockingObject 結構](cordebugblockingobject-structure.md)清單提供枚舉器。</span><span class="sxs-lookup"><span data-stu-id="0c415-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="0c415-149">[ICorDebugBox值介面](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-150">`ICorDebugHeapValue` 的子類別，表示 Boxed 值的類別物件。</span><span class="sxs-lookup"><span data-stu-id="0c415-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="0c415-151">[ICorDebug中斷點介面](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="0c415-152">表示函式中的中斷點，或是某個值上的監看點。</span><span class="sxs-lookup"><span data-stu-id="0c415-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="0c415-153">[ICorDebug突破點Enum介面](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-154">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugBreakpoint` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="0c415-155">[ICorDebug鏈介面](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="0c415-156">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="0c415-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="0c415-157">[ICorDebugChainEnum 介面](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-158">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugChain` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="0c415-159">[ICorDebug 類介面](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="0c415-160">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="0c415-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0c415-161">如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="0c415-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="0c415-162">[ICorDebugClass2 介面](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="0c415-163">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="0c415-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="0c415-164">這個介面延伸 `ICorDebugClass`。</span><span class="sxs-lookup"><span data-stu-id="0c415-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="0c415-165">[ICorDebugCode介面](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="0c415-166">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="0c415-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="0c415-167">[ICorDebugCode2 介面](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="0c415-168">提供方法來擴充 `ICorDebugCode` 的功能。</span><span class="sxs-lookup"><span data-stu-id="0c415-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="0c415-169">[ICorDebugCode3 介面](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="0c415-170">提供擴展[ICorDebugCode 和](icordebugcode-interface1.md) [ICorDebugCode2](icordebugcode2-interface.md)的方法，以提供有關託管傳回值的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="0c415-171">[ICorDebugCode4 介面](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="0c415-172">提供一種方法，使調試器能夠枚舉函數中的區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="0c415-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="0c415-173">[ICorDebugCodeEnum 介面](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-174">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugCode` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="0c415-175">[ICorDebugcom物件值介面](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-176">提供擷取快取介面物件的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="0c415-177">[ICorDebug上下文介面](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="0c415-178">表示內容物件。</span><span class="sxs-lookup"><span data-stu-id="0c415-178">Represents a context object.</span></span> <span data-ttu-id="0c415-179">尚未實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="0c415-180">[ICorDebug控制器介面](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="0c415-181">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="0c415-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="0c415-182">[ICorDebug資料目標介面](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="0c415-183">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="0c415-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="0c415-184">[ICorDebugDataTarget2 介面](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="0c415-185">從邏輯上講擴展[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="0c415-186">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-187">[ICorDebugDataTarget3 介面](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="0c415-188">從邏輯上講[，ICorDebugDataTarget](icordebugdatatarget-interface.md)介面可以提供有關已載入模組的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="0c415-189">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-190">[ICorDebugevent 介面](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="0c415-191">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="0c415-192">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-193">[ICordebugedit 和繼續錯誤資訊介面](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="0c415-194">已過時。</span><span class="sxs-lookup"><span data-stu-id="0c415-194">Obsolete.</span></span> <span data-ttu-id="0c415-195">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="0c415-196">[ICordebugedit 並繼續快照介面](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="0c415-197">已過時。</span><span class="sxs-lookup"><span data-stu-id="0c415-197">Obsolete.</span></span> <span data-ttu-id="0c415-198">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="0c415-199">[ICorDebugEnum 介面](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="0c415-200">當做抽象基底介面來偵錯列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="0c415-201">[ICorDebug錯誤資訊資訊介面](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-202">已過時。</span><span class="sxs-lookup"><span data-stu-id="0c415-202">Obsolete.</span></span> <span data-ttu-id="0c415-203">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="0c415-204">[ICorDebugEval 介面](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="0c415-205">提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c415-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="0c415-206">[ICorDebugEval2 介面](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="0c415-207">擴充 `ICorDebugEval` 來提供泛型類型的支援。</span><span class="sxs-lookup"><span data-stu-id="0c415-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="0c415-208">[ICorDebugException調試事件介面](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="0c415-209">擴展[ICorDebugDebugEvent 介面](icordebugdebugevent-interface.md)以支援異常事件。</span><span class="sxs-lookup"><span data-stu-id="0c415-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="0c415-210">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-211">[ICorDebugException 物件調用StackEnum介面](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-212">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="0c415-213">[ICorDebugException 物件值介面](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-214">擴展[ICorDebugObjectValue](icordebugobjectvalue-interface.md)介面，從託管異常物件提供堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="0c415-215">[ICorDebugFrame 介面](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="0c415-216">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="0c415-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="0c415-217">[ICorDebugFrameenum 介面](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-218">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugFrame` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="0c415-219">[ICorDebug功能介面](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="0c415-220">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="0c415-221">[ICorDebug功能2介面](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="0c415-222">以邏輯方式擴充 `ICorDebugFunction`，為 Just My Code 逐步執行的偵錯提供支援。</span><span class="sxs-lookup"><span data-stu-id="0c415-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="0c415-223">[ICorDebug功能3介面](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="0c415-224">從邏輯上講[，ICorDebug函數](icordebugfunction-interface1.md)介面提供從 ReJIT 請求對代碼的訪問。</span><span class="sxs-lookup"><span data-stu-id="0c415-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="0c415-225">[ICorDebug功能中斷點介面](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="0c415-226">擴充 `ICorDebugBreakpoint` 來支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0c415-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="0c415-227">[ICorDebugGC參考介面](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-228">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="0c415-229">[ICorDebug 通用值介面](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-230">套用至所有值之 `ICorDebugValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="0c415-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="0c415-231">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="0c415-232">[ICordebugguidtotypeenum 介面](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-233">為對應 GUID 和其相應 `ICorDebugType` 物件的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="0c415-234">[ICorDebugHandle值介面](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-235">`ICorDebugReferenceValue` 的子類別，表示偵錯工具已建立記憶體回收控制代碼的參考值。</span><span class="sxs-lookup"><span data-stu-id="0c415-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="0c415-236">[ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-237">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="0c415-238">[ICorDebugHeap分段介面](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-239">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="0c415-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="0c415-240">[ICorDebugHeap值介面](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-241">`ICorDebugValue` 的子類別，表示 CLR 記憶體回收行程所回收的物件。</span><span class="sxs-lookup"><span data-stu-id="0c415-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="0c415-242">[ICorDebugHeapValue2 介面](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="0c415-243">`ICorDebugHeapValue` 的擴充，其支援執行階段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0c415-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="0c415-244">[ICorDebugHeapValue3 介面](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="0c415-245">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="0c415-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="0c415-246">[ICorDebugIL代碼介面](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="0c415-247">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="0c415-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="0c415-248">[ICorDebugILCode2 介面](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="0c415-249">從邏輯上講[，ICorDebugILCode](icordebugilcode-interface.md)介面提供返回函數的本地變數簽名的權杖的方法，並將探測器的檢測中間語言 （IL） 偏移映射到原始方法 IL 偏移量。</span><span class="sxs-lookup"><span data-stu-id="0c415-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="0c415-250">[ICorDebugIL框架介面](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="0c415-251">表示 MSIL 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="0c415-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="0c415-252">[ICorDebugILFrame2 介面](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="0c415-253">`ICorDebugILFrame` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="0c415-254">[ICorDebugILFrame3 介面](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="0c415-255">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="0c415-256">[ICorDebugILFrame4 介面](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="0c415-257">提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c415-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="0c415-258">參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c415-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="0c415-259">[ICorDebug實例欄位符號介面](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="0c415-260">代表執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="0c415-261">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-262">[ICorDebug 內部框架介面](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="0c415-263">識別偵錯工具的框架類型。</span><span class="sxs-lookup"><span data-stu-id="0c415-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="0c415-264">[ICorDebug 內部框架2介面](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="0c415-265">提供有關內部幀的資訊，包括堆疊位址和相對於[ICorDebugFrame](icordebugframe-interface.md)物件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c415-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="0c415-266">[ICorDebugLoaded模組介面](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="0c415-267">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-267">Provides information about a loaded module.</span></span> <span data-ttu-id="0c415-268">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-269">[ICorDebug 託管回檔介面](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="0c415-270">提供方法來處理偵錯工具回呼。</span><span class="sxs-lookup"><span data-stu-id="0c415-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="0c415-271">[ICorDebug 託管回檔2介面](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="0c415-272">提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0c415-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="0c415-273">`ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="0c415-274">[ICorDebug 託管回檔3介面](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="0c415-275">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="0c415-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="0c415-276">[ICordebugMDA 介面](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="0c415-277">表示 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="0c415-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="0c415-278">[ICorDebug記憶體緩衝器介面](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="0c415-279">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c415-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="0c415-280">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-281">[ICorDebug 合併裝配記錄介面](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="0c415-282">提供合併組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="0c415-283">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-284">[ICorDebugMetaDataLocator介面](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="0c415-285">提供中繼資料資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0c415-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="0c415-286">[ICorDebug模組介面](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="0c415-287">表示 CLR 模組，其為可執行檔或動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="0c415-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="0c415-288">[ICorDebugModule2 介面](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="0c415-289">當做 `ICorDebugModule` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="0c415-290">[ICorDebug模組3介面](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="0c415-291">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="0c415-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="0c415-292">[ICorDebug模組中斷點介面](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="0c415-293">擴充 `ICorDebugBreakpoint`，以提供特定模組的存取權。</span><span class="sxs-lookup"><span data-stu-id="0c415-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="0c415-294">[ICorDebugModule調試事件介面](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="0c415-295">擴展[ICorDebugDebugEvent 介面](icordebugdebugevent-interface.md)以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="0c415-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="0c415-296">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-297">[ICorDebugModuleEnum 介面](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-298">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugModule` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="0c415-299">[ICorDebugMutable資料目標介面](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="0c415-300">擴展[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面以支援可變數據目標。</span><span class="sxs-lookup"><span data-stu-id="0c415-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="0c415-301">[ICorDebug本機框架介面](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="0c415-302">用於原生框架的 `ICorDebugFrame` 特定實作。</span><span class="sxs-lookup"><span data-stu-id="0c415-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="0c415-303">[ICorDebug本機框架2介面](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="0c415-304">提供測試父子框架關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="0c415-305">[ICorDebugObjectEnum 介面](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-306">實作 `ICorDebugEnum` 方法，並根據物件陣列的相對虛擬位址 (RVA) 來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="0c415-307">[ICorDebug物件值介面](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-308">`ICorDebugValue` 的子類別，表示包含物件的值。</span><span class="sxs-lookup"><span data-stu-id="0c415-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="0c415-309">[ICorDebug物件值2介面](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="0c415-310">擴充 `ICorDebugObjectValue` 來支援繼承和覆寫。</span><span class="sxs-lookup"><span data-stu-id="0c415-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="0c415-311">[ICorDebug進程介面](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="0c415-312">表示執行 Managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="0c415-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="0c415-313">[ICorDebugProcess2 介面](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="0c415-314">`ICorDebugProcess` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="0c415-315">[ICorDebugProcess3 介面](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="0c415-316">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="0c415-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="0c415-317">[ICorDebugProcess4 介面](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="0c415-318">支援進程執行失控。</span><span class="sxs-lookup"><span data-stu-id="0c415-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="0c415-319">[ICorDebugProcess5 介面](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="0c415-320">擴展[ICorDebugProcess](icordebugprocess-interface.md)介面以支援對託管堆的訪問，提供有關託管物件的垃圾回收的資訊，並確定調試器是否從應用程式的本地本機映射緩存載入圖像。</span><span class="sxs-lookup"><span data-stu-id="0c415-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="0c415-321">[ICorDebugProcess6 介面](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="0c415-322">從邏輯上講擴展[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用在本機異常調試事件中編碼的託管調試事件解碼和虛擬模組拆分等功能。</span><span class="sxs-lookup"><span data-stu-id="0c415-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="0c415-323">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-324">[ICorDebugProcess7 介面](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="0c415-325">提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。</span><span class="sxs-lookup"><span data-stu-id="0c415-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="0c415-326">[ICorDebugProcess8 介面](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="0c415-327">從邏輯上講擴展[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用或禁用某些類型的[ICorDebug 託管回檔2](icordebugmanagedcallback2-interface.md)異常回檔。</span><span class="sxs-lookup"><span data-stu-id="0c415-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="0c415-328">[ICorDebugProcessEnum 介面](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-329">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugProcess` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="0c415-330">[ICorDebug參考值介面](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-331">支援參考類型的 `ICorDebugValue` 子類別。</span><span class="sxs-lookup"><span data-stu-id="0c415-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="0c415-332">[ICorDebug註冊集介面](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="0c415-333">表示目前在機器上執行程式碼的可用暫存器集合。</span><span class="sxs-lookup"><span data-stu-id="0c415-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="0c415-334">[ICorDebug註冊集2介面](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="0c415-335">為具有 64 個以上暫存器的硬體平台，擴充 `ICorDebugRegisterSet` 的功能。</span><span class="sxs-lookup"><span data-stu-id="0c415-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="0c415-336">[ICorDebug遠端介面](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="0c415-337">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="0c415-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="0c415-338">[ICorDebug遠端目標介面](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="0c415-339">提供可讓您對 CLR 環境中的 Silverlight 應用程式進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="0c415-340">[ICorDebug運行時可展開幀介面](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="0c415-341">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="0c415-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="0c415-342">[ICorDebugStackWalk介面](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="0c415-343">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="0c415-344">[ICorDebug靜態欄位符號介面](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="0c415-345">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="0c415-346">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-347">[ICorDebug步進器介面](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="0c415-348">表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。</span><span class="sxs-lookup"><span data-stu-id="0c415-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="0c415-349">[ICorDebug步進2介面](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="0c415-350">提供 Just My Code (JMC) 偵錯的支援。</span><span class="sxs-lookup"><span data-stu-id="0c415-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="0c415-351">[ICorDebug步進介面](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-352">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugStepper` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="0c415-353">[ICorDebugString值介面](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-354">套用至字串值之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="0c415-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="0c415-355">[ICorDebug符號提供程式介面](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="0c415-356">提供可用來擷取偵錯符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="0c415-357">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-358">[ICorDebug符號提供程式2介面](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="0c415-359">從邏輯上講，擴展[ICorDebugSymbolProvider 介面](icordebugsymbolprovider-interface.md)以檢索其他調試符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="0c415-360">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-361">[ICorDebug執行緒介面](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="0c415-362">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0c415-362">Represents a thread in a process.</span></span> <span data-ttu-id="0c415-363">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="0c415-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="0c415-364">[ICorDebugThread2 介面](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="0c415-365">當做 `ICorDebugThread` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0c415-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="0c415-366">[ICorDebugThread3 介面](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="0c415-367">提供[ICorDebugStackWalk](icordebugstackwalk-interface.md)的進入點和相應的介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="0c415-368">[ICorDebugThread4 介面](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="0c415-369">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="0c415-370">[ICorDebugThreadenum 介面](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="0c415-371">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugThread` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="0c415-372">[ICorDebug 類型介面](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="0c415-373">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="0c415-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0c415-374">如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="0c415-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="0c415-375">[ICorDebugType2 介面](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="0c415-376">擴展[ICorDebugType](icordebugtype-interface.md)介面以檢索基本類型或複雜（使用者定義）類型的類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="0c415-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="0c415-377">[ICorDebugTypeEnum 介面](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-378">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugType` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="0c415-379">[ICorDebugUn託管回檔介面](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="0c415-380">提供未直接與 CLR 有關之原生事件的告知。</span><span class="sxs-lookup"><span data-stu-id="0c415-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="0c415-381">[ICorDebug值](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="0c415-382">表示所偵錯之處理序中的讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="0c415-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="0c415-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="0c415-384">擴充 `ICorDebugValue` 來提供 `ICorDebugType` 的支援。</span><span class="sxs-lookup"><span data-stu-id="0c415-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="0c415-385">[ICorDebugValue3 介面](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="0c415-386">擴展"ICorDebugValue"和"ICorDebugValue2"介面，為大於 2 GB 的陣列提供支援。</span><span class="sxs-lookup"><span data-stu-id="0c415-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="0c415-387">[ICorDebugValue突破點](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="0c415-388">擴充 `ICorDebugBreakpoint`，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="0c415-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="0c415-389">[ICorDebugValueenum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-390">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugValue` 陣列。</span><span class="sxs-lookup"><span data-stu-id="0c415-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="0c415-391">[ICorDebug可變家庭介面](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="0c415-392">表示函數的區域變數或參數。</span><span class="sxs-lookup"><span data-stu-id="0c415-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="0c415-393">[ICorDebug可變家庭介面](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-394">向函數中的區域變數和參數提供枚舉器。</span><span class="sxs-lookup"><span data-stu-id="0c415-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="0c415-395">[ICorDebug可變符號介面](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="0c415-396">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="0c415-397">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-398">[ICorDebug虛擬釋放器介面](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="0c415-399">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="0c415-400">**僅適用於 .NET 原生。**</span><span class="sxs-lookup"><span data-stu-id="0c415-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="0c415-401">[ICorPublish 介面](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="0c415-402">當做發行處理序的一般介面。</span><span class="sxs-lookup"><span data-stu-id="0c415-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="0c415-403">[ICor發佈應用域介面](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="0c415-404">表示及提供與應用程式定義域有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c415-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="0c415-405">[ICorPublishAppDomainEnum 介面](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-406">提供方法來周遊目前存在於處理序中之 `ICorPublishAppDomain` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="0c415-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="0c415-407">[ICorPublishEnum 介面](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-408">當做發行列舉值的抽象基底。</span><span class="sxs-lookup"><span data-stu-id="0c415-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="0c415-409">[ICor發佈過程介面](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="0c415-410">提供存取處理序相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="0c415-411">[ICorPublishProcessEnum 介面](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="0c415-412">提供方法來周遊 `ICorPublishProcess` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="0c415-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="0c415-413">[ISOSDac介面介面](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="0c415-414">提供從 訪問資料的協助程式方法`SOS`。</span><span class="sxs-lookup"><span data-stu-id="0c415-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="0c415-415">[IXCLRData方法定義介面](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="0c415-416">提供查詢有關方法定義的資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="0c415-417">[IXCLRData方法實例介面](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="0c415-418">提供查詢方法實例資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="0c415-419">[IXCLR資料模組介面](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="0c415-420">提供查詢有關載入模組的資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="0c415-421">[IXCLR資料處理介面](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="0c415-422">提供了查詢有關進程的資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="0c415-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="0c415-423">相關章節</span><span class="sxs-lookup"><span data-stu-id="0c415-423">Related Sections</span></span>  
 <span data-ttu-id="0c415-424">[調試同類](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="0c415-425">[調試全域靜態函數](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="0c415-426">[調試枚舉](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="0c415-427">[調試結構](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="0c415-427">[Debugging Structures](debugging-structures.md)</span></span>\
