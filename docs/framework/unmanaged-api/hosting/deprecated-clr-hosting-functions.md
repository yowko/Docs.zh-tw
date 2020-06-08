---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504364"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="adc5e-102">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="adc5e-103">本節說明舊版裝載 API 所使用的非受控全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="adc5e-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="adc5e-104">除了僅供 .NET Framework 使用的基礎結構函式（ `_Cor*` 函數）之外，這些函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="adc5e-105">啟用函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-105">Activation functions</span></span>  
 [<span data-ttu-id="adc5e-106">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="adc5e-107">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-107">Deprecated.</span></span> <span data-ttu-id="adc5e-108">建立指定之 managed 類型的實例。</span><span class="sxs-lookup"><span data-stu-id="adc5e-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="adc5e-109">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="adc5e-110">已過時。</span><span class="sxs-lookup"><span data-stu-id="adc5e-110">Obsolete.</span></span> <span data-ttu-id="adc5e-111">若要初始化 common language runtime （CLR），請使用[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="adc5e-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="adc5e-112">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="adc5e-113">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-113">Deprecated.</span></span> <span data-ttu-id="adc5e-114">確保 CLR 執行引擎已載入進程中。</span><span class="sxs-lookup"><span data-stu-id="adc5e-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="adc5e-115">請改用[ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="adc5e-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="adc5e-116">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="adc5e-117">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-117">Deprecated.</span></span> <span data-ttu-id="adc5e-118">使用儲存在 XML 檔案中的版本資訊，將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="adc5e-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="adc5e-119">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="adc5e-120">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-120">Deprecated.</span></span> <span data-ttu-id="adc5e-121">可讓非受控主機將 CLR 載入進程中。</span><span class="sxs-lookup"><span data-stu-id="adc5e-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="adc5e-122">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="adc5e-123">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-123">Deprecated.</span></span> <span data-ttu-id="adc5e-124">使用從 XML 檔案讀取的版本資訊，將 CLR 載入進程中。</span><span class="sxs-lookup"><span data-stu-id="adc5e-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="adc5e-125">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="adc5e-126">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-126">Deprecated.</span></span> <span data-ttu-id="adc5e-127">可讓非受控主機將 CLR 載入進程，並可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="adc5e-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="adc5e-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="adc5e-129">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-129">Deprecated.</span></span> <span data-ttu-id="adc5e-130">讓主機能夠將指定的 CLR 版本載入進程中。</span><span class="sxs-lookup"><span data-stu-id="adc5e-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="adc5e-131">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="adc5e-132">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-132">Deprecated.</span></span> <span data-ttu-id="adc5e-133">取得所需的 CLR 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="adc5e-134">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="adc5e-135">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-135">Deprecated.</span></span> <span data-ttu-id="adc5e-136">傳回載入進程之 CLR 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="adc5e-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="adc5e-137">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="adc5e-138">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-138">Deprecated.</span></span> <span data-ttu-id="adc5e-139">取得從 CLR 的最新已安裝版本匯出之指定函式的位址。</span><span class="sxs-lookup"><span data-stu-id="adc5e-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="adc5e-140">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="adc5e-141">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-141">Deprecated.</span></span> <span data-ttu-id="adc5e-142">取得應用程式所要求之 CLR 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="adc5e-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="adc5e-143">CLR 版本函數</span><span class="sxs-lookup"><span data-stu-id="adc5e-143">CLR version functions</span></span>  
 <span data-ttu-id="adc5e-144">本節中的函式會傳回 CLR 版本;它們不會啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="adc5e-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="adc5e-145">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="adc5e-146">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-146">Deprecated.</span></span> <span data-ttu-id="adc5e-147">傳回目前進程中正在執行之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="adc5e-148">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="adc5e-149">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-149">Deprecated.</span></span> <span data-ttu-id="adc5e-150">使用指定的緩衝區，取得指定檔案的 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="adc5e-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="adc5e-151">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="adc5e-152">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-152">Deprecated.</span></span> <span data-ttu-id="adc5e-153">取得指定的應用程式所要求之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="adc5e-154">如果未安裝該版本，會取得所要求版本之前所安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="adc5e-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="adc5e-155">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="adc5e-156">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-156">Deprecated.</span></span> <span data-ttu-id="adc5e-157">使用指定的 CLSID，取得類別的適當 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="adc5e-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="adc5e-158">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="adc5e-159">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-159">Deprecated.</span></span> <span data-ttu-id="adc5e-160">取得與指定的進程控制碼相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="adc5e-161">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="adc5e-162">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-162">Deprecated.</span></span> <span data-ttu-id="adc5e-163">允許主機判斷在明確初始化 CLR 之前，將在進程中使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="adc5e-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="adc5e-164">裝載函數</span><span class="sxs-lookup"><span data-stu-id="adc5e-164">Hosting functions</span></span>  
 [<span data-ttu-id="adc5e-165">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="adc5e-166">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-166">Deprecated.</span></span> <span data-ttu-id="adc5e-167">呼叫在指定的程式庫中具有指定名稱和參數的函式。</span><span class="sxs-lookup"><span data-stu-id="adc5e-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="adc5e-168">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="adc5e-169">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-169">Deprecated.</span></span> <span data-ttu-id="adc5e-170">從進程中卸載 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="adc5e-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="adc5e-171">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="adc5e-172">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-172">Deprecated.</span></span> <span data-ttu-id="adc5e-173">關閉目前的非受控進程。</span><span class="sxs-lookup"><span data-stu-id="adc5e-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="adc5e-174">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="adc5e-175">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-175">Deprecated.</span></span> <span data-ttu-id="adc5e-176">使用指定的資訊清單和其他應用程式資料，在指定的網路路徑啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="adc5e-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="adc5e-177">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="adc5e-178">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-178">Deprecated.</span></span> <span data-ttu-id="adc5e-179">標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="adc5e-180">從 .NET Framework 版本2.0 開始，此函式不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="adc5e-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="adc5e-181">這不是必要的，而且可以從程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="adc5e-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="adc5e-182">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="adc5e-183">已過時。</span><span class="sxs-lookup"><span data-stu-id="adc5e-183">Obsolete.</span></span> <span data-ttu-id="adc5e-184">CLR 無法從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="adc5e-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="adc5e-185">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="adc5e-186">已過時。</span><span class="sxs-lookup"><span data-stu-id="adc5e-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="adc5e-187">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="adc5e-188">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-188">Deprecated.</span></span> <span data-ttu-id="adc5e-189">根據指定的版本資訊建立[ICorDebug](../debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="adc5e-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="adc5e-190">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="adc5e-191">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-191">Deprecated.</span></span> <span data-ttu-id="adc5e-192">建立[ICeeFileGen](iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="adc5e-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="adc5e-193">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="adc5e-194">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-194">Deprecated.</span></span> <span data-ttu-id="adc5e-195">終結[ICeeFileGen](iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="adc5e-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="adc5e-196">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="adc5e-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="adc5e-197">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-197">Deprecated.</span></span> <span data-ttu-id="adc5e-198">指向 CLR 所呼叫的函式，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="adc5e-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="adc5e-199">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="adc5e-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="adc5e-200">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-200">Deprecated.</span></span> <span data-ttu-id="adc5e-201">指向 CLR 呼叫的函式，以通知主機初始化已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="adc5e-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="adc5e-202">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="adc5e-203">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-203">Deprecated.</span></span> <span data-ttu-id="adc5e-204">取得介面的指標，允許 CLR 管理身分識別。</span><span class="sxs-lookup"><span data-stu-id="adc5e-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="adc5e-205">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="adc5e-206">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-206">Deprecated.</span></span> <span data-ttu-id="adc5e-207">載入指定的 .NET Framework DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="adc5e-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="adc5e-208">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="adc5e-209">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-209">Deprecated.</span></span> <span data-ttu-id="adc5e-210">使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="adc5e-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="adc5e-211">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="adc5e-212">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-212">Deprecated.</span></span> <span data-ttu-id="adc5e-213">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="adc5e-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="adc5e-214">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="adc5e-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="adc5e-215">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-215">Deprecated.</span></span> <span data-ttu-id="adc5e-216">指向函式，當裝置的重迭（也就是非同步） i/o 完成時，會通知主機。</span><span class="sxs-lookup"><span data-stu-id="adc5e-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="adc5e-217">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="adc5e-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="adc5e-218">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-218">Deprecated.</span></span> <span data-ttu-id="adc5e-219">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="adc5e-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="adc5e-220">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="adc5e-221">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-221">Deprecated.</span></span> <span data-ttu-id="adc5e-222">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="adc5e-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="adc5e-223">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="adc5e-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="adc5e-224">已被取代。</span><span class="sxs-lookup"><span data-stu-id="adc5e-224">Deprecated.</span></span> <span data-ttu-id="adc5e-225">指向函式，該函式會通知主機等候控制碼已發出信號或已超時。</span><span class="sxs-lookup"><span data-stu-id="adc5e-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="adc5e-226">基礎結構函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-226">Infrastructure functions</span></span>  
 <span data-ttu-id="adc5e-227">本節中的函數僅供 .NET Framework 使用。</span><span class="sxs-lookup"><span data-stu-id="adc5e-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="adc5e-228">_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="adc5e-229">初始化 CLR，尋找 DLL 元件的 CLR 標頭中的 managed 進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="adc5e-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="adc5e-230">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="adc5e-231">初始化 CLR，尋找可執行元件的 CLR 標頭中的 managed 進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="adc5e-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="adc5e-232">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="adc5e-233">執行指定的記憶體對應程式碼中的進入點。</span><span class="sxs-lookup"><span data-stu-id="adc5e-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="adc5e-234">此函式是由作業系統載入器所呼叫。</span><span class="sxs-lookup"><span data-stu-id="adc5e-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="adc5e-235">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="adc5e-236">卸載受管理的模組映射時，通知載入器。</span><span class="sxs-lookup"><span data-stu-id="adc5e-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="adc5e-237">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="adc5e-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="adc5e-238">驗證受管理的模組映射，並在載入作業系統載入器之後通知它。</span><span class="sxs-lookup"><span data-stu-id="adc5e-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc5e-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc5e-239">See also</span></span>

- [<span data-ttu-id="adc5e-240">裝載全域靜態函式的 .NET Framework 4 </span><span class="sxs-lookup"><span data-stu-id="adc5e-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
