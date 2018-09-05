---
title: 診斷 Managed 偵錯助理的錯誤
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532971"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="f2221-102">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="f2221-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="f2221-103">Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2221-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="f2221-104">這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="f2221-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="f2221-105">您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="f2221-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="f2221-106">您可以[啟用或停用](#enable-and-disable-mdas)加入至 Windows 登錄機碼，或藉由設定環境變數的所有 Mda。</span><span class="sxs-lookup"><span data-stu-id="f2221-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="f2221-107">若要啟用特定 MDA，您可以使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="f2221-108">您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="f2221-109">因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="f2221-110">您不能為已啟動的應用程式啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="f2221-111">下表列出.NET framework 隨附的 Mda:</span><span class="sxs-lookup"><span data-stu-id="f2221-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="f2221-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="f2221-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="f2221-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="f2221-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="f2221-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="f2221-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="f2221-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="f2221-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="f2221-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="f2221-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="f2221-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="f2221-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="f2221-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="f2221-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="f2221-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="f2221-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="f2221-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="f2221-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="f2221-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="f2221-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="f2221-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="f2221-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="f2221-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="f2221-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="f2221-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="f2221-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="f2221-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f2221-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="f2221-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="f2221-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="f2221-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="f2221-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="f2221-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="f2221-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="f2221-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="f2221-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="f2221-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="f2221-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="f2221-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="f2221-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="f2221-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="f2221-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="f2221-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="f2221-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="f2221-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="f2221-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="f2221-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="f2221-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="f2221-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="f2221-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="f2221-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="f2221-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="f2221-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="f2221-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="f2221-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="f2221-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="f2221-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="f2221-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="f2221-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="f2221-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="f2221-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="f2221-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="f2221-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="f2221-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="f2221-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="f2221-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="f2221-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="f2221-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="f2221-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="f2221-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="f2221-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="f2221-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="f2221-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="f2221-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="f2221-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="f2221-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="f2221-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="f2221-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="f2221-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="f2221-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="f2221-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="f2221-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="f2221-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="f2221-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="f2221-154">根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。</span><span class="sxs-lookup"><span data-stu-id="f2221-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="f2221-155">您可以檢視的預設集在 Visual Studio 中選擇**Windows** > **例外狀況設定**上**偵錯**功能表，然後再展開**Managed 偵錯助理**清單。</span><span class="sxs-lookup"><span data-stu-id="f2221-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![在 Visual Studio 中的例外狀況設定視窗](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="f2221-157">啟用和停用 Mda</span><span class="sxs-lookup"><span data-stu-id="f2221-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="f2221-158">若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="f2221-159">您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="f2221-160">而不是停用 Mda，您可以防止 Visual Studio 時收到 MDA 通知時顯示 MDA 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2221-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="f2221-161">若要這樣做，請選擇**Windows** > **例外狀況設定**上**偵錯**功能表中，展開  **Managed 偵錯助理**清單，然後選取或清除**中斷時擲回**核取方塊，針對個別的 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="f2221-162">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="f2221-162">Registry Key</span></span>

<span data-ttu-id="f2221-163">若要啟用 Mda，新增**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\MDA**子機碼 （類型 REG_SZ，值 1） 在 Windows 登錄中的。</span><span class="sxs-lookup"><span data-stu-id="f2221-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="f2221-164">將下列範例複製到名為文字檔*MDAEnable.reg*。開啟 Windows 登錄編輯程式 (RegEdit.exe)，以及從**檔案**功能表中選擇 **匯入**。</span><span class="sxs-lookup"><span data-stu-id="f2221-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="f2221-165">選取  *MDAEnable.reg*檔，以便在該電腦上啟用 Mda。</span><span class="sxs-lookup"><span data-stu-id="f2221-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="f2221-166">將子機碼設定為字串值**1** (不是 DWORD 值的**1**) 可讓讀取 MDA 設定從*ApplicationName.suffix*.mda.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2221-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="f2221-167">例如，[記事本] 的 MDA 組態檔會命名為 notepad.exe.mda.config。</span><span class="sxs-lookup"><span data-stu-id="f2221-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="f2221-168">如果電腦是在 64 位元作業系統上執行 32 位元應用程式，則應將 MDA 機碼設定如下：</span><span class="sxs-lookup"><span data-stu-id="f2221-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="f2221-169">請參閱[應用程式特定組態設定](#application-specific-configuration-settings)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f2221-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="f2221-170">COMPLUS_MDA 環境變數可以覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="f2221-171">請參閱[環境變數](#environment-variable)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f2221-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="f2221-172">若要停用 Mda，將 MDA 子機碼設為**0**使用 Windows 登錄編輯程式 （零）。</span><span class="sxs-lookup"><span data-stu-id="f2221-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="f2221-173">根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。</span><span class="sxs-lookup"><span data-stu-id="f2221-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="f2221-174">您可以藉由執行停用這些助理*MDADisable.reg*檔案，如本節稍早所述。</span><span class="sxs-lookup"><span data-stu-id="f2221-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="f2221-175">環境變數</span><span class="sxs-lookup"><span data-stu-id="f2221-175">Environment Variable</span></span>

<span data-ttu-id="f2221-176">MDA 的啟用也可以由環境變數 COMPLUS_MDA 來控制，它會覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f2221-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="f2221-177">COMPLUS_MDA 字串是 MDA 名稱或其他特殊控制項字串的清單，不區分大小寫，並以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="f2221-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="f2221-178">在 Managed 或 Unmanaged 偵錯工具之下啟動時，會依預設啟用一組 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="f2221-179">其做法是在環境變數或登錄機碼的值前面，隱含附加在偵錯工具之下依預設啟用的 MDA 清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="f2221-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="f2221-180">特殊控制項字串如下：</span><span class="sxs-lookup"><span data-stu-id="f2221-180">The special control strings are the following:</span></span>

- <span data-ttu-id="f2221-181">`0` - 停用所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="f2221-182">`1` - 從 *ApplicationName*.mda.config 讀取 MDA 設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="f2221-183">`managedDebugger` - 明確啟用在偵錯工具之下啟動 Managed 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="f2221-184">`unmanagedDebugger` - 明確啟用在偵錯工具之下啟動 Unmanaged 可執行檔時，隱含啟用的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="f2221-185">如果有設定相衝突，最新的設定會覆寫先前的設定：</span><span class="sxs-lookup"><span data-stu-id="f2221-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="f2221-186">`COMPLUS_MDA=0` 會停用所有 MDA，包括在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="f2221-187">`COMPLUS_MDA=gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，以及在偵錯工具之下隱含啟用的任何 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="f2221-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，但會停用在偵錯工具之下隱含啟用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="f2221-189">應用程式特定的組態設定</span><span class="sxs-lookup"><span data-stu-id="f2221-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="f2221-190">您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。</span><span class="sxs-lookup"><span data-stu-id="f2221-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="f2221-191">若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。</span><span class="sxs-lookup"><span data-stu-id="f2221-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="f2221-192">應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f2221-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="f2221-193">檔名採用 *ApplicationName*.mda.config 格式；例如，notepad.exe.mda.config。應用程式組態檔中啟用的助理可能會有為了控制該助理行為而特別設計的屬性或項目。</span><span class="sxs-lookup"><span data-stu-id="f2221-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="f2221-194">下列範例示範如何啟用及設定[封送處理](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="f2221-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

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

<span data-ttu-id="f2221-195">`Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f2221-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="f2221-196">`Marshaling` MDA 也可以篩選方法的名稱和結構欄位中提供**methodFilter**並**fieldFilter**個子項目，分別。</span><span class="sxs-lookup"><span data-stu-id="f2221-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="f2221-197">下列範例示範如何使用其預設設定來啟用多個 Mda:</span><span class="sxs-lookup"><span data-stu-id="f2221-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="f2221-198">當您在組態檔中指定多個助理時，必須依字母順序將其列出。</span><span class="sxs-lookup"><span data-stu-id="f2221-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="f2221-199">例如，如果您想要啟用 `virtualCERCall` 和 `invalidCERCall` MDA ，則必須在 `<invalidCERCall />` 項目前面加入 `<virtualCERCall />` 項目。</span><span class="sxs-lookup"><span data-stu-id="f2221-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="f2221-200">如果這些項目沒有依照字母順序，就會顯示未處理的無效組態檔例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="f2221-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="f2221-201">MDA 例外狀況</span><span class="sxs-lookup"><span data-stu-id="f2221-201">MDA exceptions</span></span>

<span data-ttu-id="f2221-202">啟用 MDA 時，它仍甚至當您的程式碼不執行以偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f2221-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="f2221-203">如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2221-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="f2221-204">若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。</span><span class="sxs-lookup"><span data-stu-id="f2221-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="f2221-205">當您的程式碼執行 Visual Studio 整合式的開發環境 (IDE) 中時，您可以避免特定 MDA 事件會出現 [例外狀況] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2221-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="f2221-206">若要這樣做，請在**偵錯**功能表上，選擇**Windows** > **例外狀況設定**。</span><span class="sxs-lookup"><span data-stu-id="f2221-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="f2221-207">在 [**例外狀況設定**] 視窗中，展開**Managed 偵錯助理**清單，然後再清除**中斷時擲回**核取方塊，針對個別的 MDA。</span><span class="sxs-lookup"><span data-stu-id="f2221-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="f2221-208">您也可以使用此對話方塊來*啟用*MDA 例外狀況對話方塊的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f2221-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="f2221-209">MDA 輸出</span><span class="sxs-lookup"><span data-stu-id="f2221-209">MDA Output</span></span>

<span data-ttu-id="f2221-210">MDA 輸出會類似下列的範例中，顯示的輸出`PInvokeStackImbalance`MDA:</span><span class="sxs-lookup"><span data-stu-id="f2221-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="f2221-211">**PInvoke 函式的呼叫 ' MDATest ！MDATest.Program::StdCall' 有不對稱的堆疊。這可能是因為 managed 的 PInvoke 簽章與未受管理的目標簽章不相符。請檢查的呼叫慣例和 PInvoke 簽章的參數相符的目標 unmanaged 簽章。**</span><span class="sxs-lookup"><span data-stu-id="f2221-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="f2221-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2221-212">See also</span></span>

- [<span data-ttu-id="f2221-213">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="f2221-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
