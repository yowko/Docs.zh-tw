---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 9e19502672973f292991b72c7ea9b4fdc17f5707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673120"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="61c47-102">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="61c47-102">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="61c47-103">本節說明舊版裝載 API 所使用的非受控全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="61c47-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="61c47-104">除了基礎結構函式以外 (函式 `_Cor*`) （僅供 .NET Framework 使用），這些函式在 .NET Framework 4 中已經被取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="61c47-105">啟用函式</span><span class="sxs-lookup"><span data-stu-id="61c47-105">Activation functions</span></span>  

 [<span data-ttu-id="61c47-106">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="61c47-107">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-107">Deprecated.</span></span> <span data-ttu-id="61c47-108">建立指定之 managed 類型的實例。</span><span class="sxs-lookup"><span data-stu-id="61c47-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="61c47-109">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="61c47-110">已過時。</span><span class="sxs-lookup"><span data-stu-id="61c47-110">Obsolete.</span></span> <span data-ttu-id="61c47-111">若要初始化 common language runtime (CLR) ，請使用 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 或 [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="61c47-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="61c47-112">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="61c47-113">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-113">Deprecated.</span></span> <span data-ttu-id="61c47-114">確保 CLR 執行引擎已載入至進程。</span><span class="sxs-lookup"><span data-stu-id="61c47-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="61c47-115">請改用 [ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="61c47-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="61c47-116">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="61c47-117">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-117">Deprecated.</span></span> <span data-ttu-id="61c47-118">使用儲存在 XML 檔案中的版本資訊，將 common language runtime (CLR) 載入至進程。</span><span class="sxs-lookup"><span data-stu-id="61c47-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="61c47-119">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="61c47-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-120">Deprecated.</span></span> <span data-ttu-id="61c47-121">讓非受控主機將 CLR 載入至進程。</span><span class="sxs-lookup"><span data-stu-id="61c47-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="61c47-122">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="61c47-123">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-123">Deprecated.</span></span> <span data-ttu-id="61c47-124">使用從 XML 檔案讀取的版本資訊，將 CLR 載入處理常式。</span><span class="sxs-lookup"><span data-stu-id="61c47-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="61c47-125">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="61c47-126">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-126">Deprecated.</span></span> <span data-ttu-id="61c47-127">可讓非受控主機將 CLR 載入至進程，並可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="61c47-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="61c47-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="61c47-129">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-129">Deprecated.</span></span> <span data-ttu-id="61c47-130">讓主機將指定的 CLR 版本載入至進程。</span><span class="sxs-lookup"><span data-stu-id="61c47-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="61c47-131">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="61c47-132">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-132">Deprecated.</span></span> <span data-ttu-id="61c47-133">取得所需的 CLR 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="61c47-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="61c47-134">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="61c47-135">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-135">Deprecated.</span></span> <span data-ttu-id="61c47-136">傳回載入至進程的 CLR 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="61c47-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="61c47-137">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="61c47-138">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-138">Deprecated.</span></span> <span data-ttu-id="61c47-139">取得從最新安裝的 CLR 版本匯出的指定函式位址。</span><span class="sxs-lookup"><span data-stu-id="61c47-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="61c47-140">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="61c47-141">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-141">Deprecated.</span></span> <span data-ttu-id="61c47-142">取得應用程式所要求之 CLR 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="61c47-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="61c47-143">CLR 版本函數</span><span class="sxs-lookup"><span data-stu-id="61c47-143">CLR version functions</span></span>  

 <span data-ttu-id="61c47-144">本節中的函式會傳回 CLR 版本;它們不會啟用 CLR。</span><span class="sxs-lookup"><span data-stu-id="61c47-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="61c47-145">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="61c47-146">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-146">Deprecated.</span></span> <span data-ttu-id="61c47-147">傳回目前進程中正在執行之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="61c47-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="61c47-148">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="61c47-149">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-149">Deprecated.</span></span> <span data-ttu-id="61c47-150">使用指定的緩衝區，取得指定之檔案的 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="61c47-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="61c47-151">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="61c47-152">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-152">Deprecated.</span></span> <span data-ttu-id="61c47-153">取得指定之應用程式所要求之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="61c47-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="61c47-154">如果未安裝該版本，則會取得在要求的版本之前安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="61c47-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="61c47-155">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="61c47-156">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-156">Deprecated.</span></span> <span data-ttu-id="61c47-157">取得具有指定 CLSID 之類別的適當 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="61c47-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="61c47-158">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="61c47-159">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-159">Deprecated.</span></span> <span data-ttu-id="61c47-160">取得與指定之進程控制碼相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="61c47-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="61c47-161">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="61c47-162">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-162">Deprecated.</span></span> <span data-ttu-id="61c47-163">允許主機在明確初始化 CLR 之前，判斷要在進程中使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="61c47-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="61c47-164">裝載函數</span><span class="sxs-lookup"><span data-stu-id="61c47-164">Hosting functions</span></span>  

 [<span data-ttu-id="61c47-165">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="61c47-166">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-166">Deprecated.</span></span> <span data-ttu-id="61c47-167">呼叫函式，該函式在指定的程式庫中具有指定的名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="61c47-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="61c47-168">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="61c47-169">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-169">Deprecated.</span></span> <span data-ttu-id="61c47-170">卸載進程中的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="61c47-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="61c47-171">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="61c47-172">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-172">Deprecated.</span></span> <span data-ttu-id="61c47-173">關閉目前未受管理的進程。</span><span class="sxs-lookup"><span data-stu-id="61c47-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="61c47-174">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="61c47-175">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-175">Deprecated.</span></span> <span data-ttu-id="61c47-176">使用指定的資訊清單和其他應用程式資料，在指定的網路路徑上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="61c47-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="61c47-177">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="61c47-178">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-178">Deprecated.</span></span> <span data-ttu-id="61c47-179">標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="61c47-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="61c47-180">從 .NET Framework 版本2.0 開始，此函數沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="61c47-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="61c47-181">這並不是必要的，而且可以從程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="61c47-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="61c47-182">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="61c47-183">已過時。</span><span class="sxs-lookup"><span data-stu-id="61c47-183">Obsolete.</span></span> <span data-ttu-id="61c47-184">CLR 無法從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="61c47-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="61c47-185">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="61c47-186">已過時。</span><span class="sxs-lookup"><span data-stu-id="61c47-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="61c47-187">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="61c47-188">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-188">Deprecated.</span></span> <span data-ttu-id="61c47-189">根據指定的版本資訊建立 [ICorDebug](../debugging/icordebug-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="61c47-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="61c47-190">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="61c47-191">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-191">Deprecated.</span></span> <span data-ttu-id="61c47-192">建立 [ICeeFileGen](iceefilegen-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="61c47-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="61c47-193">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="61c47-194">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-194">Deprecated.</span></span> <span data-ttu-id="61c47-195">終結 [ICeeFileGen](iceefilegen-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="61c47-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="61c47-196">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="61c47-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="61c47-197">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-197">Deprecated.</span></span> <span data-ttu-id="61c47-198">指向 CLR 呼叫以執行 managed 程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="61c47-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="61c47-199">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="61c47-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="61c47-200">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-200">Deprecated.</span></span> <span data-ttu-id="61c47-201">指向 CLR 呼叫的函式，以通知主機初始化已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="61c47-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="61c47-202">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="61c47-203">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-203">Deprecated.</span></span> <span data-ttu-id="61c47-204">取得介面的指標，該介面可讓 CLR 管理身分識別。</span><span class="sxs-lookup"><span data-stu-id="61c47-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="61c47-205">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="61c47-206">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-206">Deprecated.</span></span> <span data-ttu-id="61c47-207">載入指定的 .NET Framework DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="61c47-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="61c47-208">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="61c47-209">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-209">Deprecated.</span></span> <span data-ttu-id="61c47-210">使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="61c47-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="61c47-211">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="61c47-212">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-212">Deprecated.</span></span> <span data-ttu-id="61c47-213">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="61c47-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="61c47-214">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="61c47-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="61c47-215">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-215">Deprecated.</span></span> <span data-ttu-id="61c47-216">指向函式，此函式會在重迭 (（也就是對裝置的非同步) i/o 完成）時通知主機。</span><span class="sxs-lookup"><span data-stu-id="61c47-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="61c47-217">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="61c47-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="61c47-218">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-218">Deprecated.</span></span> <span data-ttu-id="61c47-219">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="61c47-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="61c47-220">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="61c47-221">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-221">Deprecated.</span></span> <span data-ttu-id="61c47-222">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="61c47-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="61c47-223">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="61c47-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="61c47-224">已取代。</span><span class="sxs-lookup"><span data-stu-id="61c47-224">Deprecated.</span></span> <span data-ttu-id="61c47-225">指向函式，該函式會通知主機等候控制碼已發出信號或已超時。</span><span class="sxs-lookup"><span data-stu-id="61c47-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="61c47-226">基礎結構函式</span><span class="sxs-lookup"><span data-stu-id="61c47-226">Infrastructure functions</span></span>  

 <span data-ttu-id="61c47-227">本節中的函數僅供 .NET Framework 使用。</span><span class="sxs-lookup"><span data-stu-id="61c47-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="61c47-228">_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="61c47-229">初始化 CLR、找出 DLL 元件的 CLR 標頭中的 managed 進入點，然後開始執行。</span><span class="sxs-lookup"><span data-stu-id="61c47-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="61c47-230">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="61c47-231">初始化 CLR、找出可執行元件的 CLR 標頭中的 managed 進入點，然後開始執行。</span><span class="sxs-lookup"><span data-stu-id="61c47-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="61c47-232">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="61c47-233">執行指定之記憶體對應程式碼中的進入點。</span><span class="sxs-lookup"><span data-stu-id="61c47-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="61c47-234">作業系統載入器會呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="61c47-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="61c47-235">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="61c47-236">卸載受控模組映射時，通知載入器。</span><span class="sxs-lookup"><span data-stu-id="61c47-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="61c47-237">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="61c47-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="61c47-238">驗證受管理的模組映射，並在載入作業系統載入器之後通知作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="61c47-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c47-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c47-239">See also</span></span>

- [<span data-ttu-id="61c47-240">裝載全域靜態函式的 .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="61c47-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
