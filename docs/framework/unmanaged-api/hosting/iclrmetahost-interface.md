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
ms.openlocfilehash: 75c8d550e572795a291f4639f9f28bd5214ff188
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714012"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="5f8b9-102">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="5f8b9-102">ICLRMetaHost Interface</span></span>

<span data-ttu-id="5f8b9-103">提供方法，這些方法會根據其版本號碼傳回特定版本的 common language runtime (CLR) 、列出所有已安裝的 Clr、列出在指定進程中載入的所有執行時間、探索用來編譯元件的 CLR 版本、找出用來編譯元件的 CLR 版本、結束具有正常執行時間關機的進程，以及查詢舊版 API 系結。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f8b9-104">方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-104">Methods</span></span>  
  
|<span data-ttu-id="5f8b9-105">方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-105">Method</span></span>|<span data-ttu-id="5f8b9-106">描述</span><span class="sxs-lookup"><span data-stu-id="5f8b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f8b9-107">EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-107">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="5f8b9-108">傳回列舉，其中包含電腦上所安裝之每個 CLR 版本的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面指標。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="5f8b9-109">EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-109">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="5f8b9-110">傳回列舉，其中包含在給定進程中載入的每個 CLR 的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面指標。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="5f8b9-111">這個方法會取代 [GetVersionFromProcess](getversionfromprocess-function.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="5f8b9-112">ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-112">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="5f8b9-113">嘗試正常關閉所有載入的執行時間，然後終止進程。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="5f8b9-114">取代 [CorExitProcess](corexitprocess-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="5f8b9-115">GetRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-115">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="5f8b9-116">取得對應至特定 CLR 版本的 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-116">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="5f8b9-117">這個方法會取代搭配[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)旗標使用的[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-117">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="5f8b9-118">GetVersionFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-118">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="5f8b9-119">取得元件的原始 .NET Framework 編譯版本 (儲存在中繼資料) 中（指定其檔案路徑）。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="5f8b9-120">這個方法會取代 [GetFileVersion](getfileversion-function.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="5f8b9-121">QueryLegacyV2RuntimeBinding 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-121">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="5f8b9-122">傳回介面，這個介面表示舊版啟用原則已系結的執行時間，例如，藉由使用 `useLegacyV2RuntimeActivationPolicy` 專案設定檔[ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)案專案上的屬性、直接使用舊版啟用 api，或藉由呼叫[ICLRRuntimeInfo：： BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="5f8b9-123">RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="5f8b9-123">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="5f8b9-124">當 CLR 版本第一次載入但尚未啟動時，保證指定函式指標的回呼。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="5f8b9-125">這個方法會取代 [LockClrVersion](lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="5f8b9-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f8b9-126">備註</span><span class="sxs-lookup"><span data-stu-id="5f8b9-126">Remarks</span></span>  

 <span data-ttu-id="5f8b9-127">取得這個介面實例的唯一方法，就是呼叫 [CLRCreateInstance](clrcreateinstance-function.md) 函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5f8b9-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5f8b9-128">需求</span><span class="sxs-lookup"><span data-stu-id="5f8b9-128">Requirements</span></span>  

 <span data-ttu-id="5f8b9-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8b9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f8b9-130">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="5f8b9-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5f8b9-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5f8b9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f8b9-132">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f8b9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8b9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f8b9-133">See also</span></span>

- [<span data-ttu-id="5f8b9-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5f8b9-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="5f8b9-135">裝載</span><span class="sxs-lookup"><span data-stu-id="5f8b9-135">Hosting</span></span>](index.md)
