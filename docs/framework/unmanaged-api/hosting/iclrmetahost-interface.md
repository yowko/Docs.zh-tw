---
title: ICLRMetaHost 介面
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45089d1b64264e000c07603808f0c5fb1263b042
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776580"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="1ebf0-102">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="1ebf0-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="1ebf0-103">提供方法，傳回 common language runtime (CLR) 的特定版本，其版本號碼為基礎，列出所有已安裝的 Clr，清單中指定的處理序所載入的所有執行階段中，探索用來編譯組件、 結束處理程序的 CLR 版本與全新的執行階段關閉舊版 API 繫結的查詢。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ebf0-104">方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-104">Methods</span></span>  
  
|<span data-ttu-id="1ebf0-105">方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-105">Method</span></span>|<span data-ttu-id="1ebf0-106">描述</span><span class="sxs-lookup"><span data-stu-id="1ebf0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ebf0-107">EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="1ebf0-108">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個 CLR 版本安裝在電腦上的介面指標。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="1ebf0-109">EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="1ebf0-110">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)載入指定的處理序中每個 CLR 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="1ebf0-111">這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="1ebf0-112">ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="1ebf0-113">嘗試先關閉所有已載入的執行階段依正常程序，然後終止處理序。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="1ebf0-114">會取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="1ebf0-115">GetRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="1ebf0-116">取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面會對應到特定的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="1ebf0-117">這個方法會取代[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)搭配使用函式[STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)旗標。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="1ebf0-118">GetVersionFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="1ebf0-119">取得組件的原始.NET Framework 編譯版本 （儲存於中繼資料），提供其檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="1ebf0-120">這個方法會取代[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="1ebf0-121">QueryLegacyV2RuntimeBinding 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="1ebf0-122">傳回代表舊版啟用原則具有已繫結至，例如使用執行階段介面`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔項目，直接使用舊版啟用的 Api，或藉由呼叫[ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="1ebf0-123">RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="1ebf0-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="1ebf0-124">第一次載入，但尚未開始的 CLR 版本時，可確保指定的函式指標的回呼。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="1ebf0-125">這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="1ebf0-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ebf0-126">備註</span><span class="sxs-lookup"><span data-stu-id="1ebf0-126">Remarks</span></span>  
 <span data-ttu-id="1ebf0-127">取得這個介面的執行個體的唯一方式是藉由呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ebf0-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1ebf0-128">需求</span><span class="sxs-lookup"><span data-stu-id="1ebf0-128">Requirements</span></span>  
 <span data-ttu-id="1ebf0-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ebf0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ebf0-130">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1ebf0-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1ebf0-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ebf0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ebf0-132">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ebf0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebf0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ebf0-133">See also</span></span>

- [<span data-ttu-id="1ebf0-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1ebf0-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1ebf0-135">裝載</span><span class="sxs-lookup"><span data-stu-id="1ebf0-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
