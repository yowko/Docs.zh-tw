---
title: "診斷 Managed 偵錯助理的錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a96068412f05d48b8b006385c66f3efbbf9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a><span data-ttu-id="e5806-102">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="e5806-102">Diagnosing Errors with Managed Debugging Assistants</span></span>
<span data-ttu-id="e5806-103">Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e5806-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="e5806-104">這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="e5806-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="e5806-105">您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="e5806-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span> <span data-ttu-id="e5806-106">若要啟用或停用所有 MDA，您可以加入機碼至 Windows 登錄，或是設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="e5806-106">You can enable or disable all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="e5806-107">若要啟用特定 MDA，您可以使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="e5806-108">您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="e5806-109">因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="e5806-110">您不能為已啟動的應用程式啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-110">You cannot enable it for applications that have already started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5806-111">當 MDA 啟用時，即使程式碼不是在偵錯工具之下執行，MDA 仍有效。</span><span class="sxs-lookup"><span data-stu-id="e5806-111">When an MDA is enabled, it is active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="e5806-112">如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e5806-112">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="e5806-113">若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-113">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5806-114">當程式碼在 Visual Studio 整合式開發環境 (IDE) 中執行時，可以避免因特定 MDA 事件而出現的例外狀況對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e5806-114">When your code is executing in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="e5806-115">若要這樣做，請在 [偵錯] 功能表中按一下 [例外狀況]。</span><span class="sxs-lookup"><span data-stu-id="e5806-115">To do that, on the **Debug** menu, click **Exceptions**.</span></span> <span data-ttu-id="e5806-116">(如果 [偵錯] 功能表沒有包含 [例外狀況] 命令，請按一下 [工具] 功能表上的 [自訂] 來新增該命令。)在 [例外狀況] 對話方塊中，展開 [Managed 偵錯助理] 清單，然後針對個別的 MDA，清除 [擲回] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e5806-116">(If the **Debug** menu does not contain an **Exceptions** command, click **Customize** on the **Tools** menu to add it.) In the **Exceptions** dialog box, expand the **Managed Debugging Assistants** list, and then clear the **Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="e5806-117">例如，若要避免 [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) 的例外狀況對話方塊，請在 [Managed 偵錯助理] 清單中，清除其名稱旁邊的 [擲回] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e5806-117">For example, to avoid the exception dialog box for a [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) clear the **Thrown** check box next to its name in the **Managed Debugging Assistants** list.</span></span> <span data-ttu-id="e5806-118">您也可以使用這個對話方塊來啟用 MDA 例外狀況對話方塊的顯示。</span><span class="sxs-lookup"><span data-stu-id="e5806-118">You can also use this dialog box to enable the display of MDA exception dialog boxes.</span></span>  
  
 <span data-ttu-id="e5806-119">下表列出 .NET Framework 隨附的 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-119">The following table lists the MDAs that ship with the .NET Framework.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="e5806-120">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="e5806-120">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="e5806-121">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="e5806-121">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[<span data-ttu-id="e5806-122">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="e5806-122">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="e5806-123">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="e5806-123">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[<span data-ttu-id="e5806-124">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="e5806-124">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="e5806-125">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="e5806-125">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[<span data-ttu-id="e5806-126">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="e5806-126">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="e5806-127">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="e5806-127">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[<span data-ttu-id="e5806-128">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="e5806-128">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="e5806-129">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="e5806-129">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[<span data-ttu-id="e5806-130">failedQI</span><span class="sxs-lookup"><span data-stu-id="e5806-130">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="e5806-131">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="e5806-131">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[<span data-ttu-id="e5806-132">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="e5806-132">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="e5806-133">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="e5806-133">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[<span data-ttu-id="e5806-134">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="e5806-134">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="e5806-135">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="e5806-135">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[<span data-ttu-id="e5806-136">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="e5806-136">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="e5806-137">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="e5806-137">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[<span data-ttu-id="e5806-138">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="e5806-138">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="e5806-139">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="e5806-139">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[<span data-ttu-id="e5806-140">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="e5806-140">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="e5806-141">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="e5806-141">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[<span data-ttu-id="e5806-142">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="e5806-142">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="e5806-143">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="e5806-143">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[<span data-ttu-id="e5806-144">loaderLock</span><span class="sxs-lookup"><span data-stu-id="e5806-144">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="e5806-145">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="e5806-145">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[<span data-ttu-id="e5806-146">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="e5806-146">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="e5806-147">marshaling</span><span class="sxs-lookup"><span data-stu-id="e5806-147">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[<span data-ttu-id="e5806-148">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="e5806-148">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="e5806-149">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="e5806-149">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[<span data-ttu-id="e5806-150">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="e5806-150">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="e5806-151">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="e5806-151">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[<span data-ttu-id="e5806-152">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="e5806-152">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="e5806-153">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="e5806-153">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[<span data-ttu-id="e5806-154">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="e5806-154">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="e5806-155">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="e5806-155">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[<span data-ttu-id="e5806-156">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="e5806-156">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="e5806-157">reentrancy</span><span class="sxs-lookup"><span data-stu-id="e5806-157">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[<span data-ttu-id="e5806-158">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="e5806-158">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="e5806-159">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="e5806-159">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[<span data-ttu-id="e5806-160">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="e5806-160">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="e5806-161">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="e5806-161">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 <span data-ttu-id="e5806-162">根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。</span><span class="sxs-lookup"><span data-stu-id="e5806-162">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="e5806-163">您可以按一下 [偵錯] 功能表上的 [例外狀況]，然後展開 [Managed 偵錯助理] 清單，即可檢視 Visual Studio 中的預設集。</span><span class="sxs-lookup"><span data-stu-id="e5806-163">You can view the default set in Visual Studio by clicking **Exceptions** on the **Debug** menu and expanding the **Managed Debugging Assistants** list.</span></span>  
  
## <a name="enabling-and-disabling-mdas"></a><span data-ttu-id="e5806-164">啟用和停用 MDA</span><span class="sxs-lookup"><span data-stu-id="e5806-164">Enabling and Disabling MDAs</span></span>  
 <span data-ttu-id="e5806-165">若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-165">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="e5806-166">您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-166">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>  
  
 <span data-ttu-id="e5806-167">在 Visual Studio 2005 (含) 以後版本中，當裝載處理序啟用時，即無法停用預設集中的 MDA，或是啟用不在預設集中的 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-167">In Visual Studio 2005 and later versions, when the hosting process is enabled, you cannot disable MDAs that are in the default set or enable MDAs that are not in the default set.</span></span> <span data-ttu-id="e5806-168">預設會啟用裝載處理序，所以必須明確將其停用。</span><span class="sxs-lookup"><span data-stu-id="e5806-168">The hosting process is enabled by default, so it must be explicitly disabled.</span></span>  
  
 <span data-ttu-id="e5806-169">若要停用 Visual Studio 中的裝載處理序，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e5806-169">To disable the hosting process in Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="e5806-170">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="e5806-170">In **Solution Explorer**, select a project.</span></span>  
  
2.  <span data-ttu-id="e5806-171">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e5806-171">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="e5806-172">[專案設計工具] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e5806-172">The **Project Designer** window appears.</span></span>  
  
3.  <span data-ttu-id="e5806-173">按一下 [偵錯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5806-173">Click the **Debug** tab.</span></span>  
  
4.  <span data-ttu-id="e5806-174">在 [啟用偵錯工具] 區段中，清除 [啟用 Visual Studio 裝載處理序] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e5806-174">In the **Enable Debuggers** section, clear the **Enable the Visual Studio hosting process** check box.</span></span>  
  
 <span data-ttu-id="e5806-175">不過，停用裝載處理序會影響效能。</span><span class="sxs-lookup"><span data-stu-id="e5806-175">However, disabling the hosting process can affect performance.</span></span> <span data-ttu-id="e5806-176">只要防止 Visual Studio 在每次收到 MDA 通知時顯示 MDA 對話方塊，就可以不需要停用 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-176">You can avoid the need to disable MDAs by preventing Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="e5806-177">若要這樣做，請在 [偵錯] 功能表上按一下 [例外狀況]，展開 [Managed 偵錯助理] 清單，然後針對個別的 MDA，清除 [擲回] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e5806-177">To do that, click **Exceptions** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Thrown** check box for the individual MDA.</span></span>  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a><span data-ttu-id="e5806-178">使用登錄機碼來啟用和停用 MDA</span><span class="sxs-lookup"><span data-stu-id="e5806-178">Enabling and Disabling MDAs by Using a Registry Key</span></span>  
 <span data-ttu-id="e5806-179">您可在 Windows 登錄中新增 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA 子機碼 (類型 REG_SZ，值 1)，啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-179">You can enable MDAs by adding the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="e5806-180">將下列範例複製到名為 MDAEnable.reg 的文字檔中。開啟 Windows 登錄編輯程式 (RegEdit.exe)，從 [檔案] 功能表中選擇 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="e5806-180">Copy the following example into a text file named MDAEnable.reg. Open the Windows Registry Editor (RegEdit.exe) and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="e5806-181">選取 MDAEnable.reg 檔案，以在該電腦上啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-181">Select the MDAEnable.reg  file to enable MDAs on that computer.</span></span> <span data-ttu-id="e5806-182">將子機碼設為字串值 1 (不是 DWORD 值 1) 即可啟用從 *ApplicationName.suffix*.mda.config 檔案讀取 MDA 設定的功能。</span><span class="sxs-lookup"><span data-stu-id="e5806-182">Setting the subkey to string value of 1 (not DWORD value of 1) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="e5806-183">(例如，[記事本] 的 MDA 組態檔會命名為 notepad.exe.mda.config)</span><span class="sxs-lookup"><span data-stu-id="e5806-183">(For example the MDA configuration file for Notepad would be named notepad.exe.mda.config)</span></span>  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="e5806-184">如果電腦是在 64 位元作業系統上執行 32 位元應用程式，則應將 MDA 機碼設定如下：</span><span class="sxs-lookup"><span data-stu-id="e5806-184">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="e5806-185">如需詳細資訊，請參閱[使用應用程式特定組態設定來啟用和停用 MDA](#appConfig)。</span><span class="sxs-lookup"><span data-stu-id="e5806-185">See [Enabling and Disabling MDAs by Using Application-Specific Configuration Settings](#appConfig) for more information.</span></span> <span data-ttu-id="e5806-186">COMPLUS_MDA 環境變數可以覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-186">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="e5806-187">如需詳細資訊，請參閱[使用環境變數來啟用和停用 MDA](#envVariable)。</span><span class="sxs-lookup"><span data-stu-id="e5806-187">See [Enabling and Disabling MDAs by Using an Environment Variable](#envVariable) for more information.</span></span>  
  
 <span data-ttu-id="e5806-188">若要停用 MDA，請使用 Windows 登錄編輯程式，將 MDA 子機碼設為 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="e5806-188">To disable MDAs, set the MDA subkey to 0 (zero) using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="e5806-189">根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。</span><span class="sxs-lookup"><span data-stu-id="e5806-189">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="e5806-190">這類助理的範例為 [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) 和 [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)。</span><span class="sxs-lookup"><span data-stu-id="e5806-190">Examples of such assistants are [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) and [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span></span> <span data-ttu-id="e5806-191">若要停用這些助理，您可以依照本節稍早的說明來執行 MDADisable.reg 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5806-191">You can disable these assistants by running the MDADisable.reg file as described earlier in this section.</span></span>  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a><span data-ttu-id="e5806-192">使用環境變數來啟用和停用 MDA</span><span class="sxs-lookup"><span data-stu-id="e5806-192">Enabling and Disabling MDAs by Using an Environment Variable</span></span>  
 <span data-ttu-id="e5806-193">MDA 的啟用也可以由環境變數 COMPLUS_MDA 來控制，它會覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="e5806-193">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="e5806-194">COMPLUS_MDA 字串是 MDA 名稱或其他特殊控制項字串的清單，不區分大小寫，並以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="e5806-194">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="e5806-195">在 Managed 或 Unmanaged 偵錯工具之下啟動時，會依預設啟用一組 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-195">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="e5806-196">其做法是在環境變數或登錄機碼的值前面，隱含附加在偵錯工具之下依預設啟用的 MDA 清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="e5806-196">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="e5806-197">特殊控制項字串如下：</span><span class="sxs-lookup"><span data-stu-id="e5806-197">The special control strings are the following:</span></span>  
  
-   <span data-ttu-id="e5806-198">`0` - 停用所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-198">`0` - Deactivates all MDAs.</span></span>  
  
-   <span data-ttu-id="e5806-199">`1` - 從 *ApplicationName*.mda.config 讀取 MDA 設定。</span><span class="sxs-lookup"><span data-stu-id="e5806-199">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>  
  
-   <span data-ttu-id="e5806-200">`managedDebugger` - 明確啟用在偵錯工具之下啟動 Managed 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-200">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>  
  
-   <span data-ttu-id="e5806-201">`unmanagedDebugger` - 明確啟用在偵錯工具之下啟動 Unmanaged 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-201">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>  
  
 <span data-ttu-id="e5806-202">如果有設定相衝突，最新的設定會覆寫先前的設定：</span><span class="sxs-lookup"><span data-stu-id="e5806-202">If there are conflicting settings, the most recent settings override previous settings:</span></span>  
  
-   <span data-ttu-id="e5806-203">`COMPLUS_MDA=0` 會停用所有 MDA，包括在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-203">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="e5806-204">`COMPLUS_MDA=gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，以及在偵錯工具之下隱含啟用的任何 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-204">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="e5806-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，但會停用在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a><span data-ttu-id="e5806-206">使用應用程式特定組態設定來啟用和停用 MDA</span><span class="sxs-lookup"><span data-stu-id="e5806-206">Enabling and Disabling MDAs by Using Application-Specific Configuration Settings</span></span>  
 <span data-ttu-id="e5806-207">您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。</span><span class="sxs-lookup"><span data-stu-id="e5806-207">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="e5806-208">若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。</span><span class="sxs-lookup"><span data-stu-id="e5806-208">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="e5806-209">應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e5806-209">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="e5806-210">檔名採用 *ApplicationName*.mda.config 格式；例如，notepad.exe.mda.config。應用程式組態檔中啟用的助理可能會有為了控制該助理行為而特別設計的屬性或項目。</span><span class="sxs-lookup"><span data-stu-id="e5806-210">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span> <span data-ttu-id="e5806-211">下面範例會示範如何啟用和設定[封送處理](../../../docs/framework/debug-trace-profile/marshaling-mda.md)。</span><span class="sxs-lookup"><span data-stu-id="e5806-211">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 <span data-ttu-id="e5806-212">`Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e5806-212">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="e5806-213">`Marshaling` MDA 也可以分別篩選 `<methodFilter>` 和 `<fieldFilter>` 子項目中提供的方法和結構欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e5806-213">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the `<methodFilter>` and `<fieldFilter>` child elements, respectively.</span></span>  
  
 <span data-ttu-id="e5806-214">下列範例示範如何使用預設值來啟用多個 MDA。</span><span class="sxs-lookup"><span data-stu-id="e5806-214">The following example shows how to enable multiple MDAs by using their default settings.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5806-215">當您在組態檔中指定多個助理時，必須依字母順序將其列出。</span><span class="sxs-lookup"><span data-stu-id="e5806-215">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="e5806-216">例如，如果您想要啟用 `virtualCERCall` 和 `invalidCERCall` MDA ，則必須在 `<invalidCERCall />` 項目前面加入 `<virtualCERCall />` 項目。</span><span class="sxs-lookup"><span data-stu-id="e5806-216">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="e5806-217">如果這些項目沒有依照字母順序，就會顯示未處理的無效組態檔例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="e5806-217">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>  
  
### <a name="mda-output"></a><span data-ttu-id="e5806-218">MDA 輸出</span><span class="sxs-lookup"><span data-stu-id="e5806-218">MDA Output</span></span>  
 <span data-ttu-id="e5806-219">MDA 輸出類似下列範例，會顯示 `pInvokeStackImbalance` MDA 的輸出。</span><span class="sxs-lookup"><span data-stu-id="e5806-219">MDA output is similar to the following example, which shows the output from the `pInvokeStackImbalance` MDA.</span></span>  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a><span data-ttu-id="e5806-220">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5806-220">See Also</span></span>  
 [<span data-ttu-id="e5806-221">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e5806-221">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
