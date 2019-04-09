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
ms.openlocfilehash: b0e1213128f5728f17225fbf6906d877dc64e86d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106609"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="86f89-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="86f89-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="86f89-103">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個版本的 common language runtime (CLR) 所指定的處理序中載入的介面指標。</span><span class="sxs-lookup"><span data-stu-id="86f89-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="86f89-104">這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="86f89-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f89-105">語法</span><span class="sxs-lookup"><span data-stu-id="86f89-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86f89-106">參數</span><span class="sxs-lookup"><span data-stu-id="86f89-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="86f89-107">[in]若要檢查載入的執行階段的程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="86f89-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="86f89-108">[out]<xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>的列舉型別[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應至每個 CLR 程序所載入的介面。</span><span class="sxs-lookup"><span data-stu-id="86f89-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86f89-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="86f89-109">Return Value</span></span>  
 <span data-ttu-id="86f89-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="86f89-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="86f89-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86f89-111">HRESULT</span></span>|<span data-ttu-id="86f89-112">描述</span><span class="sxs-lookup"><span data-stu-id="86f89-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86f89-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="86f89-113">S_OK</span></span>|<span data-ttu-id="86f89-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="86f89-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="86f89-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="86f89-115">E_POINTER</span></span>|`ppEnumerator` <span data-ttu-id="86f89-116">為 null。</span><span class="sxs-lookup"><span data-stu-id="86f89-116">is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86f89-117">備註</span><span class="sxs-lookup"><span data-stu-id="86f89-117">Remarks</span></span>  
 <span data-ttu-id="86f89-118">這個方法是列出所有載入執行階段，即使已載入它們已被取代的函式與這類[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="86f89-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f89-119">需求</span><span class="sxs-lookup"><span data-stu-id="86f89-119">Requirements</span></span>  
 <span data-ttu-id="86f89-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86f89-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f89-121">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="86f89-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="86f89-122">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86f89-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="86f89-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="86f89-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86f89-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86f89-124">See also</span></span>

- [<span data-ttu-id="86f89-125">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="86f89-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="86f89-126">裝載</span><span class="sxs-lookup"><span data-stu-id="86f89-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
