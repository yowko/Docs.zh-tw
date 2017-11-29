---
title: "偵錯列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c24882f2bd9819043bbc786bd2e5f35129a92744
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-enumerations"></a><span data-ttu-id="7fbef-102">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-102">Debugging Enumerations</span></span>
<span data-ttu-id="7fbef-103">本節說明偵錯 API 所使用的 Unmanaged 列舉。</span><span class="sxs-lookup"><span data-stu-id="7fbef-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7fbef-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7fbef-104">In This Section</span></span>  
 [<span data-ttu-id="7fbef-105">CLR_DEBUGGING_PROCESS_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="7fbef-106">提供值，可供[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7fbef-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="7fbef-107">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="7fbef-108">指出哪些記憶體區域呼叫[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)方法應該包含。</span><span class="sxs-lookup"><span data-stu-id="7fbef-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="7fbef-109">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="7fbef-110">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="7fbef-111">CorDebugBlockingReason 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="7fbef-112">指定給定物件上封鎖執行緒的原因。</span><span class="sxs-lookup"><span data-stu-id="7fbef-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="7fbef-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="7fbef-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="7fbef-114">指出呼叫鏈結初始化的原因。</span><span class="sxs-lookup"><span data-stu-id="7fbef-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="7fbef-115">CorDebugCodeInvokeKind 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="7fbef-116">描述匯出函式如何叫用 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7fbef-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="7fbef-117">CorDebugCodeInvokePurpose 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="7fbef-118">描述匯出函式呼叫 Managed 程式碼的原因。</span><span class="sxs-lookup"><span data-stu-id="7fbef-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="7fbef-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="7fbef-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="7fbef-120">提供可用的呼叫中的其他偵錯選項[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7fbef-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="7fbef-121">CorDebugDebugEventKind 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="7fbef-122">表示由解碼其資訊的事件類型[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7fbef-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="7fbef-123">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="7fbef-124">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="7fbef-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="7fbef-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="7fbef-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="7fbef-126">表示從進行的回呼類型[icordebugmanagedcallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)事件。</span><span class="sxs-lookup"><span data-stu-id="7fbef-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="7fbef-127">CorDebugExceptionFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="7fbef-128">提供例外狀況的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7fbef-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="7fbef-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="7fbef-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="7fbef-130">指出回呼在回溯階段期間通知的事件。</span><span class="sxs-lookup"><span data-stu-id="7fbef-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="7fbef-131">CorDebugGCType 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="7fbef-132">指出記憶體回收行程是在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="7fbef-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="7fbef-133">CorDebugGenerationTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="7fbef-134">指定 Managed 堆積上的記憶體區域產生方式。</span><span class="sxs-lookup"><span data-stu-id="7fbef-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="7fbef-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="7fbef-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="7fbef-136">指出控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="7fbef-137">CorDebugIlToNativeMappingTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="7fbef-138">指出特定範圍的原生指令是否對應於特殊程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="7fbef-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="7fbef-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="7fbef-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="7fbef-140">指出可以逐步執行的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="7fbef-141">CorDebugInterfaceVersion 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="7fbef-142">指定 .NET Framework 版本，或是引進介面之 .NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="7fbef-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="7fbef-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="7fbef-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="7fbef-144">識別堆疊框架的類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="7fbef-145">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="7fbef-146">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="7fbef-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="7fbef-147">CorDebugJITCompilerFlagsDeprecated 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="7fbef-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="7fbef-148">Obsolete.</span></span> <span data-ttu-id="7fbef-149">使用`CORDEBUG_JIT_DEFAULT`隸屬[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉改為。</span><span class="sxs-lookup"><span data-stu-id="7fbef-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="7fbef-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="7fbef-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="7fbef-151">提供如何取得指令指標 (IP) 值的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7fbef-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="7fbef-152">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="7fbef-153">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="7fbef-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="7fbef-154">CorDebugNGenPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="7fbef-155">提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。</span><span class="sxs-lookup"><span data-stu-id="7fbef-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="7fbef-156">CorDebugPlatform 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="7fbef-157">提供所使用的目標平台值[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7fbef-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="7fbef-158">CorDebugRecordFormat 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="7fbef-159">描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。</span><span class="sxs-lookup"><span data-stu-id="7fbef-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="7fbef-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="7fbef-160">CorDebugRegister</span></span>  
 <span data-ttu-id="7fbef-161">指定與給定處理器結構相關聯的暫存器。</span><span class="sxs-lookup"><span data-stu-id="7fbef-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="7fbef-162">CorDebugSetContextFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="7fbef-163">指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。</span><span class="sxs-lookup"><span data-stu-id="7fbef-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="7fbef-164">CorDebugStateChange 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="7fbef-165">描述依據處理序變更而必須捨棄的快取資料量。</span><span class="sxs-lookup"><span data-stu-id="7fbef-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="7fbef-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="7fbef-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="7fbef-167">指出個別步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="7fbef-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="7fbef-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="7fbef-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="7fbef-169">指定要偵錯的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="7fbef-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="7fbef-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="7fbef-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="7fbef-171">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="7fbef-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="7fbef-172">CorDebugUserState</span></span>  
 <span data-ttu-id="7fbef-173">指出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="7fbef-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="7fbef-174">CorGCReferenceType 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="7fbef-175">識別要進行記憶體回收的物件來源。</span><span class="sxs-lookup"><span data-stu-id="7fbef-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="7fbef-176">ILCodeKind 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="7fbef-177">提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="7fbef-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="7fbef-178">LoggingLevelEnum 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="7fbef-179">指出當 Managed 執行緒記錄事件時，寫入至事件記錄檔之描述性訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="7fbef-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="7fbef-180">LogSwitchCallReason 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="7fbef-181">指出在切換偵錯/追蹤時所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="7fbef-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="7fbef-182">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="7fbef-183">表示變數的原生的位置類型。</span><span class="sxs-lookup"><span data-stu-id="7fbef-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="7fbef-184">WriteableMetadataUpdateMode 列舉</span><span class="sxs-lookup"><span data-stu-id="7fbef-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="7fbef-185">提供值來指定偵錯工具是否可以看見對中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="7fbef-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7fbef-186">相關章節</span><span class="sxs-lookup"><span data-stu-id="7fbef-186">Related Sections</span></span>  
 [<span data-ttu-id="7fbef-187">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="7fbef-187">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="7fbef-188">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7fbef-188">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="7fbef-189">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="7fbef-189">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="7fbef-190">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="7fbef-190">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
