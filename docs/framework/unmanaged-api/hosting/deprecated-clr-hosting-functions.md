---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 62773ce526b1f21c57ab85a106708589fcf92f6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138264"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="c7756-102">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c7756-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="c7756-103">本節說明舊版裝載 API 所使用的非受控全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="c7756-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="c7756-104">除了僅供 .NET Framework 使用的基礎結構函數（`_Cor*` 函式）之外，這些函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="c7756-105">啟用函式</span><span class="sxs-lookup"><span data-stu-id="c7756-105">Activation functions</span></span>  
 [<span data-ttu-id="c7756-106">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="c7756-107">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-107">Deprecated.</span></span> <span data-ttu-id="c7756-108">建立指定之 managed 類型的實例。</span><span class="sxs-lookup"><span data-stu-id="c7756-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="c7756-109">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="c7756-110">已過時。</span><span class="sxs-lookup"><span data-stu-id="c7756-110">Obsolete.</span></span> <span data-ttu-id="c7756-111">若要初始化 common language runtime （CLR），請使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="c7756-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="c7756-112">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="c7756-113">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-113">Deprecated.</span></span> <span data-ttu-id="c7756-114">確保 CLR 執行引擎已載入進程中。</span><span class="sxs-lookup"><span data-stu-id="c7756-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="c7756-115">請改用[ICLRRuntimeHost：： Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c7756-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="c7756-116">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="c7756-117">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-117">Deprecated.</span></span> <span data-ttu-id="c7756-118">使用儲存在 XML 檔案中的版本資訊，將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="c7756-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="c7756-119">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="c7756-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-120">Deprecated.</span></span> <span data-ttu-id="c7756-121">可讓非受控主機將 CLR 載入進程中。</span><span class="sxs-lookup"><span data-stu-id="c7756-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="c7756-122">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="c7756-123">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-123">Deprecated.</span></span> <span data-ttu-id="c7756-124">使用從 XML 檔案讀取的版本資訊，將 CLR 載入進程中。</span><span class="sxs-lookup"><span data-stu-id="c7756-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="c7756-125">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="c7756-126">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-126">Deprecated.</span></span> <span data-ttu-id="c7756-127">可讓非受控主機將 CLR 載入進程，並可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="c7756-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="c7756-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="c7756-129">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-129">Deprecated.</span></span> <span data-ttu-id="c7756-130">讓主機能夠將指定的 CLR 版本載入進程中。</span><span class="sxs-lookup"><span data-stu-id="c7756-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="c7756-131">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="c7756-132">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-132">Deprecated.</span></span> <span data-ttu-id="c7756-133">取得所需的 CLR 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="c7756-134">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="c7756-135">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-135">Deprecated.</span></span> <span data-ttu-id="c7756-136">傳回載入進程之 CLR 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c7756-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="c7756-137">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="c7756-138">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-138">Deprecated.</span></span> <span data-ttu-id="c7756-139">取得從 CLR 的最新已安裝版本匯出之指定函式的位址。</span><span class="sxs-lookup"><span data-stu-id="c7756-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="c7756-140">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="c7756-141">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-141">Deprecated.</span></span> <span data-ttu-id="c7756-142">取得應用程式所要求之 CLR 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="c7756-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="c7756-143">CLR 版本函數</span><span class="sxs-lookup"><span data-stu-id="c7756-143">CLR version functions</span></span>  
 <span data-ttu-id="c7756-144">本節中的函式會傳回 CLR 版本;它們不會啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="c7756-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="c7756-145">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="c7756-146">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-146">Deprecated.</span></span> <span data-ttu-id="c7756-147">傳回目前進程中正在執行之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="c7756-148">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="c7756-149">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-149">Deprecated.</span></span> <span data-ttu-id="c7756-150">使用指定的緩衝區，取得指定檔案的 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c7756-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="c7756-151">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="c7756-152">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-152">Deprecated.</span></span> <span data-ttu-id="c7756-153">取得指定的應用程式所要求之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="c7756-154">如果未安裝該版本，會取得所要求版本之前所安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c7756-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="c7756-155">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="c7756-156">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-156">Deprecated.</span></span> <span data-ttu-id="c7756-157">使用指定的 CLSID，取得類別的適當 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c7756-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="c7756-158">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="c7756-159">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-159">Deprecated.</span></span> <span data-ttu-id="c7756-160">取得與指定的進程控制碼相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="c7756-161">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="c7756-162">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-162">Deprecated.</span></span> <span data-ttu-id="c7756-163">允許主機判斷在明確初始化 CLR 之前，將在進程中使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="c7756-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="c7756-164">裝載函數</span><span class="sxs-lookup"><span data-stu-id="c7756-164">Hosting functions</span></span>  
 [<span data-ttu-id="c7756-165">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="c7756-166">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-166">Deprecated.</span></span> <span data-ttu-id="c7756-167">呼叫在指定的程式庫中具有指定名稱和參數的函式。</span><span class="sxs-lookup"><span data-stu-id="c7756-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="c7756-168">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="c7756-169">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-169">Deprecated.</span></span> <span data-ttu-id="c7756-170">從進程中卸載 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c7756-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="c7756-171">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="c7756-172">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-172">Deprecated.</span></span> <span data-ttu-id="c7756-173">關閉目前的非受控進程。</span><span class="sxs-lookup"><span data-stu-id="c7756-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="c7756-174">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="c7756-175">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-175">Deprecated.</span></span> <span data-ttu-id="c7756-176">使用指定的資訊清單和其他應用程式資料，在指定的網路路徑啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7756-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="c7756-177">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="c7756-178">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-178">Deprecated.</span></span> <span data-ttu-id="c7756-179">標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="c7756-180">從 .NET Framework 版本2.0 開始，此函式不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c7756-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="c7756-181">這不是必要的，而且可以從程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="c7756-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="c7756-182">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="c7756-183">已過時。</span><span class="sxs-lookup"><span data-stu-id="c7756-183">Obsolete.</span></span> <span data-ttu-id="c7756-184">CLR 無法從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="c7756-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="c7756-185">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="c7756-186">已過時。</span><span class="sxs-lookup"><span data-stu-id="c7756-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="c7756-187">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="c7756-188">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-188">Deprecated.</span></span> <span data-ttu-id="c7756-189">根據指定的版本資訊建立[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="c7756-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="c7756-190">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="c7756-191">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-191">Deprecated.</span></span> <span data-ttu-id="c7756-192">建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="c7756-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="c7756-193">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="c7756-194">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-194">Deprecated.</span></span> <span data-ttu-id="c7756-195">終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="c7756-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="c7756-196">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="c7756-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="c7756-197">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-197">Deprecated.</span></span> <span data-ttu-id="c7756-198">指向 CLR 所呼叫的函式，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7756-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="c7756-199">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="c7756-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="c7756-200">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-200">Deprecated.</span></span> <span data-ttu-id="c7756-201">指向 CLR 呼叫的函式，以通知主機初始化已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="c7756-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="c7756-202">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="c7756-203">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-203">Deprecated.</span></span> <span data-ttu-id="c7756-204">取得介面的指標，允許 CLR 管理身分識別。</span><span class="sxs-lookup"><span data-stu-id="c7756-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="c7756-205">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="c7756-206">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-206">Deprecated.</span></span> <span data-ttu-id="c7756-207">載入指定的 .NET Framework DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="c7756-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="c7756-208">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="c7756-209">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-209">Deprecated.</span></span> <span data-ttu-id="c7756-210">使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c7756-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="c7756-211">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="c7756-212">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-212">Deprecated.</span></span> <span data-ttu-id="c7756-213">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c7756-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="c7756-214">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="c7756-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="c7756-215">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-215">Deprecated.</span></span> <span data-ttu-id="c7756-216">指向函式，當裝置的重迭（也就是非同步） i/o 完成時，會通知主機。</span><span class="sxs-lookup"><span data-stu-id="c7756-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="c7756-217">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="c7756-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="c7756-218">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-218">Deprecated.</span></span> <span data-ttu-id="c7756-219">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="c7756-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="c7756-220">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="c7756-221">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-221">Deprecated.</span></span> <span data-ttu-id="c7756-222">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="c7756-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="c7756-223">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="c7756-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="c7756-224">已取代。</span><span class="sxs-lookup"><span data-stu-id="c7756-224">Deprecated.</span></span> <span data-ttu-id="c7756-225">指向函式，該函式會通知主機等候控制碼已發出信號或已超時。</span><span class="sxs-lookup"><span data-stu-id="c7756-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="c7756-226">基礎結構函式</span><span class="sxs-lookup"><span data-stu-id="c7756-226">Infrastructure functions</span></span>  
 <span data-ttu-id="c7756-227">本節中的函數僅供 .NET Framework 使用。</span><span class="sxs-lookup"><span data-stu-id="c7756-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="c7756-228">_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="c7756-229">初始化 CLR，尋找 DLL 元件的 CLR 標頭中的 managed 進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="c7756-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="c7756-230">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="c7756-231">初始化 CLR，尋找可執行元件的 CLR 標頭中的 managed 進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="c7756-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="c7756-232">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="c7756-233">執行指定的記憶體對應程式碼中的進入點。</span><span class="sxs-lookup"><span data-stu-id="c7756-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="c7756-234">此函式是由作業系統載入器所呼叫。</span><span class="sxs-lookup"><span data-stu-id="c7756-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="c7756-235">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="c7756-236">卸載受管理的模組映射時，通知載入器。</span><span class="sxs-lookup"><span data-stu-id="c7756-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="c7756-237">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="c7756-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="c7756-238">驗證受管理的模組映射，並在載入作業系統載入器之後通知它。</span><span class="sxs-lookup"><span data-stu-id="c7756-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7756-239">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7756-239">See also</span></span>

- [<span data-ttu-id="c7756-240">.NET Framework 4 裝載全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="c7756-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
