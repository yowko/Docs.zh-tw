---
title: "偵錯介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e625818238a1fd18ef3885d2699e0f532efa40e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-interfaces"></a><span data-ttu-id="5f2fc-102">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-102">Debugging Interfaces</span></span>
<span data-ttu-id="5f2fc-103">本節說明 Unmanaged 介面，這類介面會處理通用語言執行平台 (CLR) 中所執行之程式的偵錯。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f2fc-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="5f2fc-104">In This Section</span></span>  
 [<span data-ttu-id="5f2fc-105">ICLRDataEnumMemoryRegions 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="5f2fc-106">提供方法來列舉呼叫端所指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="5f2fc-107">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="5f2fc-108">提供回呼方法，讓 `EnumMemoryRegions` 向偵錯工具報告嘗試列舉指定之記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="5f2fc-109">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="5f2fc-110">提供方法與目標 CLR 處理序互動。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="5f2fc-111">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="5f2fc-112">`ICLRDataTarget` 的子類別，資料存取服務層會使用它來管理目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="5f2fc-113">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="5f2fc-114">子類別[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)可提供存取例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="5f2fc-115">ICLRDebugging 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="5f2fc-116">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="5f2fc-117">ICLRDebuggingLibraryProvider 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="5f2fc-118">包含[ProvideLibrary 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)方法，就會取得程式庫提供者回呼介面，common language runtime 版本特定偵錯程式庫找到並載入需求。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="5f2fc-119">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="5f2fc-120">由資料存取服務層用來尋找目標處理序中之組件中繼資料的介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="5f2fc-121">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="5f2fc-122">提供方法讓開發人員於 CLR 環境中為應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="5f2fc-123">ICorDebugAppDomain 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="5f2fc-124">提供偵錯應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="5f2fc-125">ICorDebugAppDomain2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="5f2fc-126">提供方法來使用陣列、指標、函式指標和 ByRef 類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="5f2fc-127">這個介面是 `ICorDebugAppDomain` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="5f2fc-128">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="5f2fc-129">提供在應用程式定義域中使用 [!INCLUDE[wrt](../../../../includes/wrt-md.md)]類型的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="5f2fc-130">這個介面是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="5f2fc-131">ICorDebugAppDomain4 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="5f2fc-132">以邏輯方式擴充[ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)介面，以從 COM 可呼叫包裝函式取得 managed 的物件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="5f2fc-133">ICorDebugAppDomainEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="5f2fc-134">提供方法，此方法會傳回指定數目的 `ICorDebugAppDomain` 值 (從列舉類型中的下一個位置開始)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="5f2fc-135">ICorDebugArrayValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="5f2fc-136">表示一維或多維陣列之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="5f2fc-137">ICorDebugAssembly 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="5f2fc-138">表示組件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="5f2fc-139">ICorDebugAssembly2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="5f2fc-140">表示組件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-140">Represents an assembly.</span></span> <span data-ttu-id="5f2fc-141">這個介面是 `ICorDebugAssembly` 介面的擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="5f2fc-142">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="5f2fc-143">以邏輯方式擴充[ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)介面，以提供支援給容器組件及其所包含的組件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="5f2fc-144">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-145">ICorDebugAssemblyEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="5f2fc-146">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugAssembly` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-147">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="5f2fc-148">提供列舉值的清單[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="5f2fc-149">ICorDebugBoxValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="5f2fc-150">`ICorDebugHeapValue` 的子類別，表示 Boxed 值的類別物件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="5f2fc-151">ICorDebugBreakpoint 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="5f2fc-152">表示函式中的中斷點，或是某個值上的監看點。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="5f2fc-153">ICorDebugBreakpointEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="5f2fc-154">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugBreakpoint` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-155">ICorDebugChain 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="5f2fc-156">表示實體或邏輯呼叫堆疊的區段。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="5f2fc-157">ICorDebugChainEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="5f2fc-158">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugChain` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-159">ICorDebugClass 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="5f2fc-160">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="5f2fc-161">如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="5f2fc-162">ICorDebugClass2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="5f2fc-163">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="5f2fc-164">這個介面延伸 `ICorDebugClass`。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="5f2fc-165">ICorDebugCode 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="5f2fc-166">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="5f2fc-167">ICorDebugCode2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="5f2fc-168">提供方法來擴充 `ICorDebugCode` 的功能。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="5f2fc-169">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="5f2fc-170">提供方法，以擴充[ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)和[ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)提供 managed 傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="5f2fc-171">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="5f2fc-172">提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="5f2fc-173">ICorDebugCodeEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="5f2fc-174">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugCode` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-175">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="5f2fc-176">提供擷取快取介面物件的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="5f2fc-177">ICorDebugContext 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="5f2fc-178">表示內容物件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-178">Represents a context object.</span></span> <span data-ttu-id="5f2fc-179">尚未實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="5f2fc-180">ICorDebugController 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="5f2fc-181">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="5f2fc-182">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="5f2fc-183">提供回呼介面，該介面可供存取特定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="5f2fc-184">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="5f2fc-185">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="5f2fc-186">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-187">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="5f2fc-188">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="5f2fc-189">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-190">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="5f2fc-191">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="5f2fc-192">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-193">ICorDebugEditAndContinueErrorInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="5f2fc-194">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-194">Obsolete.</span></span> <span data-ttu-id="5f2fc-195">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="5f2fc-196">ICorDebugEditAndContinueSnapshot 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="5f2fc-197">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-197">Obsolete.</span></span> <span data-ttu-id="5f2fc-198">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="5f2fc-199">ICorDebugEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="5f2fc-200">當做抽象基底介面來偵錯列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="5f2fc-201">ICorDebugErrorInfoEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="5f2fc-202">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-202">Obsolete.</span></span> <span data-ttu-id="5f2fc-203">請勿使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="5f2fc-204">ICorDebugEval 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="5f2fc-205">提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="5f2fc-206">ICorDebugEval2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="5f2fc-207">擴充 `ICorDebugEval` 來提供泛型類型的支援。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="5f2fc-208">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="5f2fc-209">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="5f2fc-210">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-211">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="5f2fc-212">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="5f2fc-213">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="5f2fc-214">擴充[ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="5f2fc-215">ICorDebugFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="5f2fc-216">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="5f2fc-217">ICorDebugFrameEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="5f2fc-218">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugFrame` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-219">ICorDebugFunction 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="5f2fc-220">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="5f2fc-221">ICorDebugFunction2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="5f2fc-222">以邏輯方式擴充 `ICorDebugFunction`，為 Just My Code 逐步執行的偵錯提供支援。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="5f2fc-223">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="5f2fc-224">以邏輯方式擴充[ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)介面，以提供對 ReJIT 要求的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="5f2fc-225">ICorDebugFunctionBreakpoint 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="5f2fc-226">擴充 `ICorDebugBreakpoint` 來支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="5f2fc-227">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="5f2fc-228">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="5f2fc-229">ICorDebugGenericValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="5f2fc-230">套用至所有值之 `ICorDebugValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="5f2fc-231">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="5f2fc-232">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="5f2fc-233">為對應 GUID 和其相應 `ICorDebugType` 物件的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="5f2fc-234">ICorDebugHandleValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="5f2fc-235">`ICorDebugReferenceValue` 的子類別，表示偵錯工具已建立記憶體回收控制代碼的參考值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="5f2fc-236">ICorDebugHeapEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="5f2fc-237">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="5f2fc-238">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="5f2fc-239">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="5f2fc-240">ICorDebugHeapValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="5f2fc-241">`ICorDebugValue` 的子類別，表示 CLR 記憶體回收行程所回收的物件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="5f2fc-242">ICorDebugHeapValue2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="5f2fc-243">`ICorDebugHeapValue` 的擴充，其支援執行階段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="5f2fc-244">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="5f2fc-245">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="5f2fc-246">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="5f2fc-247">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="5f2fc-248">ICorDebugILCode2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="5f2fc-249">以邏輯方式擴充[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)介面，提供方法，傳回的語彙基元函式的區域變數簽章，而且，它將對應剖析工具檢測中繼語言 (IL) 位移至原始方法 IL位移。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="5f2fc-250">ICorDebugILFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="5f2fc-251">表示 MSIL 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="5f2fc-252">ICorDebugILFrame2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="5f2fc-253">`ICorDebugILFrame` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="5f2fc-254">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="5f2fc-255">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="5f2fc-256">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="5f2fc-257">提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="5f2fc-258">參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="5f2fc-259">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="5f2fc-260">代表執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="5f2fc-261">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-262">ICorDebugInternalFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="5f2fc-263">識別偵錯工具的框架類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="5f2fc-264">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="5f2fc-265">提供內部框架，包括堆疊位址和位置的相關資訊[ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="5f2fc-266">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="5f2fc-267">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-267">Provides information about a loaded module.</span></span> <span data-ttu-id="5f2fc-268">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-269">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="5f2fc-270">提供方法來處理偵錯工具回呼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="5f2fc-271">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="5f2fc-272">提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="5f2fc-273">`ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="5f2fc-274">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="5f2fc-275">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="5f2fc-276">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="5f2fc-277">表示 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="5f2fc-278">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="5f2fc-279">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="5f2fc-280">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-281">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="5f2fc-282">提供合併之組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="5f2fc-283">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-284">ICorDebugMetaDataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="5f2fc-285">提供中繼資料資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="5f2fc-286">ICorDebugModule 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="5f2fc-287">表示 CLR 模組，其為可執行檔或動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="5f2fc-288">ICorDebugModule2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="5f2fc-289">當做 `ICorDebugModule` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="5f2fc-290">ICorDebugModule3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="5f2fc-291">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="5f2fc-292">ICorDebugModuleBreakpoint 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="5f2fc-293">擴充 `ICorDebugBreakpoint`，以提供特定模組的存取權。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="5f2fc-294">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="5f2fc-295">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="5f2fc-296">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-297">ICorDebugModuleEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="5f2fc-298">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugModule` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-299">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="5f2fc-300">擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以支援可變動的資料目標。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="5f2fc-301">ICorDebugNativeFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="5f2fc-302">用於原生框架的 `ICorDebugFrame` 特定實作。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="5f2fc-303">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="5f2fc-304">提供測試父子框架關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="5f2fc-305">ICorDebugObjectEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="5f2fc-306">實作 `ICorDebugEnum` 方法，並根據物件陣列的相對虛擬位址 (RVA) 來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="5f2fc-307">ICorDebugObjectValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="5f2fc-308">`ICorDebugValue` 的子類別，表示包含物件的值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="5f2fc-309">ICorDebugObjectValue2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="5f2fc-310">擴充 `ICorDebugObjectValue` 來支援繼承和覆寫。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="5f2fc-311">ICorDebugProcess 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="5f2fc-312">表示執行 Managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="5f2fc-313">ICorDebugProcess2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="5f2fc-314">`ICorDebugProcess` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="5f2fc-315">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="5f2fc-316">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="5f2fc-317">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="5f2fc-318">擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以支援存取 managed 堆積，以提供的受管理物件，記憶體回收的相關資訊，以及判斷偵錯工具是否從應用程式載入映像的本機原生映像快取。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="5f2fc-319">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="5f2fc-320">以邏輯方式擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以啟用功能，例如解碼會以原生例外狀況偵錯事件，以及虛擬模組分割編碼的 managed 偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="5f2fc-321">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-322">ICorDebugProcess7 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="5f2fc-323">提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="5f2fc-324">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="5f2fc-325">以邏輯方式擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="5f2fc-326">ICorDebugProcessEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="5f2fc-327">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugProcess` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-328">ICorDebugReferenceValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="5f2fc-329">支援參考類型的 `ICorDebugValue` 子類別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="5f2fc-330">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="5f2fc-331">表示目前在機器上執行程式碼的可用暫存器集合。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="5f2fc-332">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="5f2fc-333">為具有 64 個以上暫存器的硬體平台，擴充 `ICorDebugRegisterSet` 的功能。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="5f2fc-334">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="5f2fc-335">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="5f2fc-336">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="5f2fc-337">提供可讓您對 CLR 環境中的 Silverlight 應用程式進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="5f2fc-338">ICorDebugRuntimeUnwindableFrame 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="5f2fc-339">提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="5f2fc-340">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="5f2fc-341">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="5f2fc-342">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="5f2fc-343">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="5f2fc-344">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-345">ICorDebugStepper 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="5f2fc-346">表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="5f2fc-347">ICorDebugStepper2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="5f2fc-348">提供 Just My Code (JMC) 偵錯的支援。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="5f2fc-349">ICorDebugStepperEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="5f2fc-350">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugStepper` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-351">ICorDebugStringValue 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="5f2fc-352">套用至字串值之 `ICorDebugHeapValue` 的子類別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="5f2fc-353">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="5f2fc-354">提供可用來擷取偵錯符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="5f2fc-355">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-356">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="5f2fc-357">以邏輯方式擴充[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)介面，以擷取其他偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="5f2fc-358">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-359">ICorDebugThread 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="5f2fc-360">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-360">Represents a thread in a process.</span></span> <span data-ttu-id="5f2fc-361">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="5f2fc-362">ICorDebugThread2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="5f2fc-363">當做 `ICorDebugThread` 的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="5f2fc-364">ICorDebugThread3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="5f2fc-365">提供的進入點[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)及對應介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="5f2fc-366">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="5f2fc-367">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="5f2fc-368">ICorDebugThreadEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="5f2fc-369">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugThread` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-370">ICorDebugType 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="5f2fc-371">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="5f2fc-372">如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="5f2fc-373">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="5f2fc-374">擴充[ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)介面擷取類型識別項的基底類型或複雜 （使用者定義） 的型別。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="5f2fc-375">ICorDebugTypeEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="5f2fc-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="5f2fc-376">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugType` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-377">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="5f2fc-378">提供未直接與 CLR 有關之原生事件的告知。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="5f2fc-379">「 ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="5f2fc-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="5f2fc-380">表示所偵錯之處理序中的讀取或寫入值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="5f2fc-381">「 ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="5f2fc-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="5f2fc-382">擴充 `ICorDebugValue` 來提供 `ICorDebugType` 的支援。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="5f2fc-383">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="5f2fc-384">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="5f2fc-385">「 ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="5f2fc-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="5f2fc-386">擴充 `ICorDebugBreakpoint`，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="5f2fc-387">「 ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="5f2fc-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="5f2fc-388">實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugValue` 陣列。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="5f2fc-389">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="5f2fc-390">代表本機變數或函式的引數。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="5f2fc-391">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="5f2fc-392">提供的本機變數和引數的函式中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="5f2fc-393">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="5f2fc-394">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="5f2fc-395">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-396">ICorDebugVirtualUnwinder 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="5f2fc-397">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="5f2fc-398">**適用於僅限.NET Native。**</span><span class="sxs-lookup"><span data-stu-id="5f2fc-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="5f2fc-399">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="5f2fc-400">當做發行處理序的一般介面。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="5f2fc-401">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="5f2fc-402">表示及提供與應用程式定義域有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="5f2fc-403">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="5f2fc-404">提供方法來周遊目前存在於處理序中之 `ICorPublishAppDomain` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="5f2fc-405">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="5f2fc-406">當做發行列舉值的抽象基底。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="5f2fc-407">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="5f2fc-408">提供存取處理序相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="5f2fc-409">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fc-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="5f2fc-410">提供方法來周遊 `ICorPublishProcess` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="5f2fc-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5f2fc-411">相關章節</span><span class="sxs-lookup"><span data-stu-id="5f2fc-411">Related Sections</span></span>  
 [<span data-ttu-id="5f2fc-412">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="5f2fc-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="5f2fc-413">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="5f2fc-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="5f2fc-414">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5f2fc-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="5f2fc-415">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="5f2fc-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
