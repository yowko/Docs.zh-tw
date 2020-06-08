---
title: ICLRMetaHost::GetRuntime 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504187"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="53bcd-102">ICLRMetaHost::GetRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="53bcd-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="53bcd-103">取得對應至特定 common language runtime （CLR）版本的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="53bcd-103">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="53bcd-104">這個方法會取代與[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)旗標搭配使用的[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="53bcd-104">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bcd-105">語法</span><span class="sxs-lookup"><span data-stu-id="53bcd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53bcd-106">參數</span><span class="sxs-lookup"><span data-stu-id="53bcd-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="53bcd-107">在儲存在中繼資料中的 .NET Framework 編譯版本，格式為 "v*A*。*B*[。*X*] "。</span><span class="sxs-lookup"><span data-stu-id="53bcd-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="53bcd-108">*A*、 *B*和*X*是對應至主要版本、次要版本和組建編號的十進位數。</span><span class="sxs-lookup"><span data-stu-id="53bcd-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53bcd-109">此參數必須符合 .NET Framework 版本的目錄名稱，因為它出現在 C:\Windows\Microsoft.NET\Framework 或 C:\Windows\Microsoft.NET\Framework64. 之下</span><span class="sxs-lookup"><span data-stu-id="53bcd-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="53bcd-110">範例值為 "v v1.0.3705"、"v 1.1.4322"、"v 2.0.50727" 和 "v4.0"。*X*"，其中*X*取決於安裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="53bcd-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="53bcd-111">需要 "v" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="53bcd-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="53bcd-112">在所需介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="53bcd-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="53bcd-113">目前，此參數唯一有效的值為 IID_ICLRRuntimeInfo。</span><span class="sxs-lookup"><span data-stu-id="53bcd-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="53bcd-114">脫銷對應至所要求執行時間之[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="53bcd-114">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53bcd-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="53bcd-115">Return Value</span></span>  
 <span data-ttu-id="53bcd-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="53bcd-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="53bcd-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53bcd-117">HRESULT</span></span>|<span data-ttu-id="53bcd-118">說明</span><span class="sxs-lookup"><span data-stu-id="53bcd-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53bcd-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="53bcd-119">S_OK</span></span>|<span data-ttu-id="53bcd-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="53bcd-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="53bcd-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="53bcd-121">E_POINTER</span></span>|<span data-ttu-id="53bcd-122">`pwzVersion` 或 `ppRuntime` 為 null。</span><span class="sxs-lookup"><span data-stu-id="53bcd-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53bcd-123">備註</span><span class="sxs-lookup"><span data-stu-id="53bcd-123">Remarks</span></span>  
 <span data-ttu-id="53bcd-124">這個方法會一致地與舊版介面互動，例如[ICorRuntimeHost](icorruntimehost-interface.md)介面和舊版函式，例如已被取代的函式 `CorBindTo*` （請參閱 .NET FRAMEWORK 2.0 裝載 API 中已[淘汰的 CLR 裝載](deprecated-clr-hosting-functions.md)函式）。</span><span class="sxs-lookup"><span data-stu-id="53bcd-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="53bcd-125">也就是說，使用舊版 API 載入的執行時間會顯示在新的 API 中，而舊版 API 也可以看到以新 API 載入的執行時間。</span><span class="sxs-lookup"><span data-stu-id="53bcd-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bcd-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="53bcd-126">Requirements</span></span>  
 <span data-ttu-id="53bcd-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53bcd-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bcd-128">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="53bcd-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53bcd-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="53bcd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53bcd-130">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bcd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bcd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53bcd-131">See also</span></span>

- [<span data-ttu-id="53bcd-132">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="53bcd-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="53bcd-133">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="53bcd-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="53bcd-134">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="53bcd-134">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="53bcd-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="53bcd-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="53bcd-136">Hosting</span><span class="sxs-lookup"><span data-stu-id="53bcd-136">Hosting</span></span>](index.md)
