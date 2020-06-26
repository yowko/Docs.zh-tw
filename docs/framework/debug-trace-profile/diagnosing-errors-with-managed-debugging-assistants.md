---
title: 診斷 Managed 偵錯助理的錯誤
description: 使用受管理的調試助理來診斷 .NET 中的錯誤。 Mda 是與 CLR 搭配運作的調試輔助工具，可提供執行時間狀態資訊。
ms.date: 08/14/2018
f1_keywords:
- EHMDA
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
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416092"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="77d30-104">使用受管理的調試助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="77d30-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="77d30-105">Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="77d30-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="77d30-106">這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="77d30-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="77d30-107">您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="77d30-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="77d30-108">您可以藉由將金鑰新增至 Windows 登錄或設定環境變數，來[啟用或停](#enable-and-disable-mdas)用所有 mda。</span><span class="sxs-lookup"><span data-stu-id="77d30-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="77d30-109">若要啟用特定 MDA，您可以使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="77d30-110">您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="77d30-111">因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="77d30-112">您不能為已啟動的應用程式啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="77d30-113">下表列出 .NET Framework 隨附的 Mda：</span><span class="sxs-lookup"><span data-stu-id="77d30-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="77d30-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="77d30-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="77d30-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="77d30-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="77d30-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="77d30-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="77d30-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="77d30-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="77d30-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="77d30-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="77d30-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="77d30-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="77d30-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="77d30-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="77d30-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="77d30-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="77d30-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="77d30-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="77d30-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="77d30-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="77d30-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="77d30-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="77d30-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="77d30-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="77d30-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="77d30-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="77d30-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="77d30-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="77d30-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="77d30-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="77d30-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="77d30-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="77d30-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="77d30-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="77d30-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="77d30-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="77d30-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="77d30-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="77d30-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="77d30-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="77d30-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="77d30-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="77d30-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="77d30-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="77d30-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="77d30-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="77d30-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="77d30-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="77d30-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="77d30-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="77d30-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="77d30-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="77d30-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="77d30-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="77d30-141">marshaling</span><span class="sxs-lookup"><span data-stu-id="77d30-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="77d30-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="77d30-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="77d30-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="77d30-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="77d30-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="77d30-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="77d30-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="77d30-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="77d30-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="77d30-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="77d30-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="77d30-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="77d30-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="77d30-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="77d30-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="77d30-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="77d30-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="77d30-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="77d30-151">入</span><span class="sxs-lookup"><span data-stu-id="77d30-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="77d30-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="77d30-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="77d30-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="77d30-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="77d30-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="77d30-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="77d30-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="77d30-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="77d30-156">根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。</span><span class="sxs-lookup"><span data-stu-id="77d30-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="77d30-157">您可以在 [偵錯工具] 功能表上選擇 [ **Windows**  >  **例外**狀況設定**Debug** ]，然後展開 [ **Managed 調試**程式] 清單，以在 Visual Studio 中查看預設集合。</span><span class="sxs-lookup"><span data-stu-id="77d30-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Visual Studio 中的 [例外狀況設定] 視窗](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="77d30-159">啟用和停用 Mda</span><span class="sxs-lookup"><span data-stu-id="77d30-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="77d30-160">若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="77d30-161">您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="77d30-162">您不需要停用 Mda，只要收到 MDA 通知，您就可以防止 Visual Studio 顯示 MDA 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="77d30-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="77d30-163">若要這麼做，請選擇 [偵錯工具] 功能表上的 [ **Windows**  >  **例外狀況設定**]，展開 [ **Managed 調試**程式] 清單，然後選取或清除個別 MDA 的 [擲回**時中斷**] 核取方塊。 **Debug**</span><span class="sxs-lookup"><span data-stu-id="77d30-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="77d30-164">登錄金鑰</span><span class="sxs-lookup"><span data-stu-id="77d30-164">Registry Key</span></span>

<span data-ttu-id="77d30-165">若要啟用 Mda，請新增**HKEY_LOCAL_MACHINE \software\microsoft \\ 。** Windows 登錄中的 NETFramework\MDA 子機碼（類型 REG_SZ，值1）。</span><span class="sxs-lookup"><span data-stu-id="77d30-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="77d30-166">將下列範例複製到名為*mdaenable.reg*的文字檔中。開啟 Windows 登錄編輯程式（RegEdit.exe），然後從 [檔案 **] 功能表選擇 [匯\*\*\*\*入**]。</span><span class="sxs-lookup"><span data-stu-id="77d30-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="77d30-167">選取 [ *mdaenable.reg* ] 檔案，以啟用該電腦上的 mda。</span><span class="sxs-lookup"><span data-stu-id="77d30-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="77d30-168">將子機碼設為字串值**1** （不是 DWORD 值**1**），可以從*ApplicationName*.mda.config 檔案讀取 MDA 設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="77d30-169">例如，[記事本] 的 MDA 設定檔會命名為 notepad.exe.mda.config。</span><span class="sxs-lookup"><span data-stu-id="77d30-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="77d30-170">如果電腦是在 64 位元作業系統上執行 32 位元應用程式，則應將 MDA 機碼設定如下：</span><span class="sxs-lookup"><span data-stu-id="77d30-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="77d30-171">如需詳細資訊，請參閱[應用程式特定的設定](#application-specific-configuration-settings)。</span><span class="sxs-lookup"><span data-stu-id="77d30-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="77d30-172">COMPLUS_MDA 環境變數可以覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="77d30-173">如需詳細資訊，請參閱[環境變數](#environment-variable)。</span><span class="sxs-lookup"><span data-stu-id="77d30-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="77d30-174">若要停用 Mda，請使用 Windows 登錄編輯程式，將 MDA 子機碼設定為**0** （零）。</span><span class="sxs-lookup"><span data-stu-id="77d30-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="77d30-175">根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。</span><span class="sxs-lookup"><span data-stu-id="77d30-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="77d30-176">如本節稍早所述，您可以執行*mdadisable.reg*來停用這些助理。</span><span class="sxs-lookup"><span data-stu-id="77d30-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="77d30-177">環境變數</span><span class="sxs-lookup"><span data-stu-id="77d30-177">Environment Variable</span></span>

<span data-ttu-id="77d30-178">MDA 的啟用也可以由環境變數 COMPLUS_MDA 來控制，它會覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="77d30-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="77d30-179">COMPLUS_MDA 字串是 MDA 名稱或其他特殊控制項字串的清單，不區分大小寫，並以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="77d30-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="77d30-180">在 Managed 或 Unmanaged 偵錯工具之下啟動時，會依預設啟用一組 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="77d30-181">其做法是在環境變數或登錄機碼的值前面，隱含附加在偵錯工具之下依預設啟用的 MDA 清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="77d30-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="77d30-182">特殊控制項字串如下：</span><span class="sxs-lookup"><span data-stu-id="77d30-182">The special control strings are the following:</span></span>

- <span data-ttu-id="77d30-183">`0` - 停用所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="77d30-184">`1` - 從 *ApplicationName*.mda.config 讀取 MDA 設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="77d30-185">`managedDebugger` - 明確啟用在偵錯工具之下啟動 Managed 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="77d30-186">`unmanagedDebugger` - 明確啟用在偵錯工具之下啟動 Unmanaged 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="77d30-187">如果有設定相衝突，最新的設定會覆寫先前的設定：</span><span class="sxs-lookup"><span data-stu-id="77d30-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="77d30-188">`COMPLUS_MDA=0` 會停用所有 MDA，包括在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="77d30-189">`COMPLUS_MDA=gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，以及在偵錯工具之下隱含啟用的任何 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="77d30-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，但會停用在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="77d30-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="77d30-191">應用程式特定的設定</span><span class="sxs-lookup"><span data-stu-id="77d30-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="77d30-192">您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。</span><span class="sxs-lookup"><span data-stu-id="77d30-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="77d30-193">若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。</span><span class="sxs-lookup"><span data-stu-id="77d30-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="77d30-194">應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="77d30-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="77d30-195">檔案名的格式為*ApplicationName*.mda.config;例如，notepad.exe.mda.config。應用程式佈建檔中啟用的助理可能會有特別設計來控制該小幫手行為的屬性或元素。</span><span class="sxs-lookup"><span data-stu-id="77d30-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="77d30-196">下列範例顯示如何啟用和設定[封送處理](marshaling-mda.md)：</span><span class="sxs-lookup"><span data-stu-id="77d30-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="77d30-197">`Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="77d30-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="77d30-198">`Marshaling`MDA 也可以分別篩選**MethodFilter**和**fieldFilter**子項目中提供的方法和結構欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="77d30-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="77d30-199">下列範例顯示如何使用預設設定來啟用多個 Mda：</span><span class="sxs-lookup"><span data-stu-id="77d30-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="77d30-200">當您在組態檔中指定多個助理時，必須依字母順序將其列出。</span><span class="sxs-lookup"><span data-stu-id="77d30-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="77d30-201">例如，如果您想要啟用 `virtualCERCall` 和 `invalidCERCall` MDA ，則必須在 `<invalidCERCall />` 項目前面加入 `<virtualCERCall />` 項目。</span><span class="sxs-lookup"><span data-stu-id="77d30-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="77d30-202">如果這些項目沒有依照字母順序，就會顯示未處理的無效組態檔例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="77d30-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="77d30-203">MDA 例外狀況</span><span class="sxs-lookup"><span data-stu-id="77d30-203">MDA exceptions</span></span>

<span data-ttu-id="77d30-204">當 MDA 啟用時，即使您的程式碼不是在偵錯工具下執行，它仍是作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="77d30-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="77d30-205">如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77d30-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="77d30-206">若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。</span><span class="sxs-lookup"><span data-stu-id="77d30-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="77d30-207">當您的程式碼在 Visual Studio 的整合式開發環境（IDE）中執行時，您可以避免出現特定 MDA 事件的例外狀況對話方塊。</span><span class="sxs-lookup"><span data-stu-id="77d30-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="77d30-208">若要這麼做，請在 [**調試**程式] 功能表上，選擇 [ **Windows**  >  **例外狀況設定**]。</span><span class="sxs-lookup"><span data-stu-id="77d30-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="77d30-209">在 [**例外狀況設定**] 視窗中，展開 [ **Managed 偵錯工具助理**] 清單，然後清除個別 MDA 的 [擲回**時中斷**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="77d30-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="77d30-210">您也可以使用此對話方塊來*啟用*[MDA 例外狀況] 對話方塊的顯示。</span><span class="sxs-lookup"><span data-stu-id="77d30-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="77d30-211">MDA 輸出</span><span class="sxs-lookup"><span data-stu-id="77d30-211">MDA Output</span></span>

<span data-ttu-id="77d30-212">MDA 輸出類似于下列範例，其會顯示來自 MDA 的輸出 `PInvokeStackImbalance` ：</span><span class="sxs-lookup"><span data-stu-id="77d30-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="77d30-213">**呼叫 PInvoke 函數 ' MDATest！MDATest 程式：： StdCall ' 的堆疊不對稱。這很可能是因為受控 PInvoke 簽章與非受控目標籤章不相符。檢查 PInvoke 簽章的呼叫慣例和參數是否符合目標非受控簽章。**</span><span class="sxs-lookup"><span data-stu-id="77d30-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="77d30-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77d30-214">See also</span></span>

- [<span data-ttu-id="77d30-215">偵錯工具、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="77d30-215">Debugging, Tracing, and Profiling</span></span>](index.md)
