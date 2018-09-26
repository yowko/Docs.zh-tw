---
title: ICLRMetaHost::EnumerateLoadedRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db10b5c67a098cc34292a2680bd832f9cef2861b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205008"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="5fdb9-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="5fdb9-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="5fdb9-103">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個版本的 common language runtime (CLR) 所指定的處理序中載入的介面指標。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="5fdb9-104">這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fdb9-105">語法</span><span class="sxs-lookup"><span data-stu-id="5fdb9-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fdb9-106">參數</span><span class="sxs-lookup"><span data-stu-id="5fdb9-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="5fdb9-107">[in]若要檢查載入的執行階段的程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="5fdb9-108">[out]<xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>的列舉型別[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應至每個 CLR 程序所載入的介面。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fdb9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5fdb9-109">Return Value</span></span>  
 <span data-ttu-id="5fdb9-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5fdb9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fdb9-111">HRESULT</span></span>|<span data-ttu-id="5fdb9-112">描述</span><span class="sxs-lookup"><span data-stu-id="5fdb9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fdb9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fdb9-113">S_OK</span></span>|<span data-ttu-id="5fdb9-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5fdb9-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5fdb9-115">E_POINTER</span></span>|<span data-ttu-id="5fdb9-116">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fdb9-117">備註</span><span class="sxs-lookup"><span data-stu-id="5fdb9-117">Remarks</span></span>  
 <span data-ttu-id="5fdb9-118">這個方法是列出所有載入執行階段，即使已載入它們已被取代的函式與這類[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fdb9-119">需求</span><span class="sxs-lookup"><span data-stu-id="5fdb9-119">Requirements</span></span>  
 <span data-ttu-id="5fdb9-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fdb9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fdb9-121">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5fdb9-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5fdb9-122">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5fdb9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fdb9-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fdb9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdb9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fdb9-124">See Also</span></span>  
 [<span data-ttu-id="5fdb9-125">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="5fdb9-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="5fdb9-126">裝載</span><span class="sxs-lookup"><span data-stu-id="5fdb9-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
