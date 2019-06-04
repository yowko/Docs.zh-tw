---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dde711f2d626d88fd80009fa83f1198dd9d47810
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490489"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="5f584-102">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="5f584-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="5f584-103">本節說明的 unmanaged 全域靜態函式舊版裝載 API 的使用。</span><span class="sxs-lookup"><span data-stu-id="5f584-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="5f584-104">基礎結構功能除外 (`_Cor*`函式)，這僅供.NET Framework、.NET Framework 4 中，這些函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="5f584-105">啟用函式</span><span class="sxs-lookup"><span data-stu-id="5f584-105">Activation functions</span></span>  
 [<span data-ttu-id="5f584-106">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="5f584-107">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-107">Deprecated.</span></span> <span data-ttu-id="5f584-108">建立指定之 managed 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f584-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="5f584-109">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="5f584-110">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f584-110">Obsolete.</span></span> <span data-ttu-id="5f584-111">若要初始化 common language runtime (CLR)，請使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或是[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="5f584-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="5f584-112">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="5f584-113">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-113">Deprecated.</span></span> <span data-ttu-id="5f584-114">可以確保 CLR 執行引擎會載入處理序。</span><span class="sxs-lookup"><span data-stu-id="5f584-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="5f584-115">使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="5f584-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="5f584-116">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="5f584-117">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-117">Deprecated.</span></span> <span data-ttu-id="5f584-118">載入處理序的 common language runtime (CLR) 使用的 XML 檔案中儲存的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5f584-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="5f584-119">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="5f584-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-120">Deprecated.</span></span> <span data-ttu-id="5f584-121">可讓 unmanaged 主應用程式將 CLR 載入處理程序。</span><span class="sxs-lookup"><span data-stu-id="5f584-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="5f584-122">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="5f584-123">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-123">Deprecated.</span></span> <span data-ttu-id="5f584-124">將 CLR 載入處理程序中，使用的讀取 XML 檔案的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5f584-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="5f584-125">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="5f584-126">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-126">Deprecated.</span></span> <span data-ttu-id="5f584-127">可讓 unmanaged 主應用程式將 CLR 載入處理序，並可讓您設定旗標指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="5f584-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="5f584-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="5f584-129">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-129">Deprecated.</span></span> <span data-ttu-id="5f584-130">可讓主機將 CLR 的指定的版本載入處理序。</span><span class="sxs-lookup"><span data-stu-id="5f584-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="5f584-131">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="5f584-132">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-132">Deprecated.</span></span> <span data-ttu-id="5f584-133">取得必要的 CLR 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5f584-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="5f584-134">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="5f584-135">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-135">Deprecated.</span></span> <span data-ttu-id="5f584-136">傳回 CLR 載入處理序的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="5f584-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="5f584-137">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="5f584-138">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-138">Deprecated.</span></span> <span data-ttu-id="5f584-139">取得指定從最新已安裝的 CLR 版本匯出的函式的位址。</span><span class="sxs-lookup"><span data-stu-id="5f584-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="5f584-140">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="5f584-141">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-141">Deprecated.</span></span> <span data-ttu-id="5f584-142">取得應用程式所要求的 CLR 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="5f584-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="5f584-143">CLR 版本函式</span><span class="sxs-lookup"><span data-stu-id="5f584-143">CLR version functions</span></span>  
 <span data-ttu-id="5f584-144">在本節中的函式傳回 CLR 版本;它們不會啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="5f584-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="5f584-145">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="5f584-146">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-146">Deprecated.</span></span> <span data-ttu-id="5f584-147">傳回在目前的處理序中執行的 clr 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5f584-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="5f584-148">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="5f584-149">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-149">Deprecated.</span></span> <span data-ttu-id="5f584-150">取得指定的檔案，並使用指定的緩衝區的 CLR 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5f584-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="5f584-151">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="5f584-152">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-152">Deprecated.</span></span> <span data-ttu-id="5f584-153">取得所指定的應用程式要求的 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5f584-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="5f584-154">如果未安裝該版本，取得要求的版本之前已安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="5f584-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="5f584-155">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="5f584-156">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-156">Deprecated.</span></span> <span data-ttu-id="5f584-157">取得適當的 CLR 版本資訊，以指定的 CLSID 類別。</span><span class="sxs-lookup"><span data-stu-id="5f584-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="5f584-158">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="5f584-159">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-159">Deprecated.</span></span> <span data-ttu-id="5f584-160">取得與指定的處理序控制代碼相關聯的 clr 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5f584-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="5f584-161">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="5f584-162">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-162">Deprecated.</span></span> <span data-ttu-id="5f584-163">可讓主應用程式判斷在處理序之前先明確初始化 CLR 用 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="5f584-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="5f584-164">裝載函式</span><span class="sxs-lookup"><span data-stu-id="5f584-164">Hosting functions</span></span>  
 [<span data-ttu-id="5f584-165">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="5f584-166">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-166">Deprecated.</span></span> <span data-ttu-id="5f584-167">會指定程式庫中具有指定的名稱和參數的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="5f584-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="5f584-168">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="5f584-169">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-169">Deprecated.</span></span> <span data-ttu-id="5f584-170">卸載 COM 組件從處理序。</span><span class="sxs-lookup"><span data-stu-id="5f584-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="5f584-171">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="5f584-172">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-172">Deprecated.</span></span> <span data-ttu-id="5f584-173">關閉目前未受管理的處理序。</span><span class="sxs-lookup"><span data-stu-id="5f584-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="5f584-174">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="5f584-175">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-175">Deprecated.</span></span> <span data-ttu-id="5f584-176">啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f584-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="5f584-177">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="5f584-178">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-178">Deprecated.</span></span> <span data-ttu-id="5f584-179">標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f584-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="5f584-180">從.NET Framework 2.0 版開始，此函式沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="5f584-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="5f584-181">它不是必要項，並可從您的程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="5f584-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="5f584-182">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="5f584-183">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f584-183">Obsolete.</span></span> <span data-ttu-id="5f584-184">CLR 無法從處理序卸載。</span><span class="sxs-lookup"><span data-stu-id="5f584-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="5f584-185">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="5f584-186">已過時。</span><span class="sxs-lookup"><span data-stu-id="5f584-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="5f584-187">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="5f584-188">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-188">Deprecated.</span></span> <span data-ttu-id="5f584-189">會建立[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件會根據指定的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5f584-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="5f584-190">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="5f584-191">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-191">Deprecated.</span></span> <span data-ttu-id="5f584-192">會建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5f584-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="5f584-193">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="5f584-194">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-194">Deprecated.</span></span> <span data-ttu-id="5f584-195">終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5f584-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="5f584-196">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="5f584-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="5f584-197">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-197">Deprecated.</span></span> <span data-ttu-id="5f584-198">指向 CLR 呼叫執行 managed 程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="5f584-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="5f584-199">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="5f584-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="5f584-200">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-200">Deprecated.</span></span> <span data-ttu-id="5f584-201">指向 CLR 呼叫以通知主機的函式初始設定已開始或完成。</span><span class="sxs-lookup"><span data-stu-id="5f584-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="5f584-202">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="5f584-203">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-203">Deprecated.</span></span> <span data-ttu-id="5f584-204">取得允許 CLR 管理身分識別的介面指標。</span><span class="sxs-lookup"><span data-stu-id="5f584-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="5f584-205">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="5f584-206">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-206">Deprecated.</span></span> <span data-ttu-id="5f584-207">載入指定的版本的.NET Framework DLL。</span><span class="sxs-lookup"><span data-stu-id="5f584-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="5f584-208">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="5f584-209">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-209">Deprecated.</span></span> <span data-ttu-id="5f584-210">使用目前執行緒的預設文化特性，將 HRESULT 值轉譯成錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5f584-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="5f584-211">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="5f584-212">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-212">Deprecated.</span></span> <span data-ttu-id="5f584-213">將 HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="5f584-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="5f584-214">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="5f584-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="5f584-215">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-215">Deprecated.</span></span> <span data-ttu-id="5f584-216">指向主應用程式時之重疊的函式 (也就是非同步) 至裝置的 I/O 已完成。</span><span class="sxs-lookup"><span data-stu-id="5f584-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="5f584-217">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="5f584-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="5f584-218">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-218">Deprecated.</span></span> <span data-ttu-id="5f584-219">指向主應用程式執行緒已開始執行的函式。</span><span class="sxs-lookup"><span data-stu-id="5f584-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="5f584-220">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="5f584-221">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-221">Deprecated.</span></span> <span data-ttu-id="5f584-222">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="5f584-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="5f584-223">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="5f584-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="5f584-224">已取代。</span><span class="sxs-lookup"><span data-stu-id="5f584-224">Deprecated.</span></span> <span data-ttu-id="5f584-225">指向主應用程式，等候控制代碼已收到信號或逾時的函式。</span><span class="sxs-lookup"><span data-stu-id="5f584-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="5f584-226">基礎結構函式</span><span class="sxs-lookup"><span data-stu-id="5f584-226">Infrastructure functions</span></span>  
 <span data-ttu-id="5f584-227">在本節中的函式會使用僅限.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="5f584-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="5f584-228">_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="5f584-229">初始化 CLR、 在 DLL 組件的 CLR 標頭，尋找 managed 的進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="5f584-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="5f584-230">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="5f584-231">初始化 CLR、 在可執行組件的 CLR 標頭，尋找 managed 的進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="5f584-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="5f584-232">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="5f584-233">指定記憶體對應的程式碼中執行的進入點。</span><span class="sxs-lookup"><span data-stu-id="5f584-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="5f584-234">作業系統載入器會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="5f584-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="5f584-235">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="5f584-236">卸載 managed 的模組映像時，請通知載入器。</span><span class="sxs-lookup"><span data-stu-id="5f584-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="5f584-237">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="5f584-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="5f584-238">驗證 managed 的模組映像，並載入後通知作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="5f584-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f584-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f584-239">See also</span></span>

- [<span data-ttu-id="5f584-240">.NET Framework 4 裝載全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="5f584-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
