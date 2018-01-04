---
title: "ICLRMetaHost::EnumerateLoadedRuntimes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaccca336fccf9ad858e2c20ee162f3dbab52224
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="cabbd-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="cabbd-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="cabbd-103">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個版本的 common language runtime (CLR) 中指定的處理序所載入的介面指標。</span><span class="sxs-lookup"><span data-stu-id="cabbd-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="cabbd-104">這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="cabbd-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabbd-105">語法</span><span class="sxs-lookup"><span data-stu-id="cabbd-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cabbd-106">參數</span><span class="sxs-lookup"><span data-stu-id="cabbd-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="cabbd-107">[in]要載入的執行階段檢查的處理序控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cabbd-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="cabbd-108">[out]<!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown`列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應至每個 CLR 程序所載入的介面。</span><span class="sxs-lookup"><span data-stu-id="cabbd-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cabbd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cabbd-109">Return Value</span></span>  
 <span data-ttu-id="cabbd-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="cabbd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cabbd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cabbd-111">HRESULT</span></span>|<span data-ttu-id="cabbd-112">描述</span><span class="sxs-lookup"><span data-stu-id="cabbd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cabbd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cabbd-113">S_OK</span></span>|<span data-ttu-id="cabbd-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="cabbd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="cabbd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cabbd-115">E_POINTER</span></span>|<span data-ttu-id="cabbd-116">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="cabbd-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cabbd-117">備註</span><span class="sxs-lookup"><span data-stu-id="cabbd-117">Remarks</span></span>  
 <span data-ttu-id="cabbd-118">這個方法是列出所有載入執行階段，即使它們已例如載入與已被取代的函式[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="cabbd-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cabbd-119">需求</span><span class="sxs-lookup"><span data-stu-id="cabbd-119">Requirements</span></span>  
 <span data-ttu-id="cabbd-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cabbd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cabbd-121">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cabbd-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cabbd-122">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cabbd-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cabbd-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cabbd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabbd-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="cabbd-124">See Also</span></span>  
 [<span data-ttu-id="cabbd-125">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="cabbd-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="cabbd-126">裝載</span><span class="sxs-lookup"><span data-stu-id="cabbd-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
