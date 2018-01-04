---
title: "ICLRMetaHost::EnumerateInstalledRuntimes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateInstalledRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41e9b9de120154fe90eb3e73ada2ced4fa3e4544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="13c4d-102">ICLRMetaHost::EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="13c4d-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="13c4d-103">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個版本的 common language runtime (CLR) 安裝在電腦上的介面。</span><span class="sxs-lookup"><span data-stu-id="13c4d-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="13c4d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="13c4d-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="13c4d-106">[out]列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面對應至每個已安裝在電腦上的 clr 版本。</span><span class="sxs-lookup"><span data-stu-id="13c4d-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c4d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="13c4d-107">Return Value</span></span>  
 <span data-ttu-id="13c4d-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="13c4d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="13c4d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13c4d-109">HRESULT</span></span>|<span data-ttu-id="13c4d-110">描述</span><span class="sxs-lookup"><span data-stu-id="13c4d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13c4d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="13c4d-111">S_OK</span></span>|<span data-ttu-id="13c4d-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="13c4d-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="13c4d-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="13c4d-113">E_POINTER</span></span>|<span data-ttu-id="13c4d-114">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="13c4d-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13c4d-115">需求</span><span class="sxs-lookup"><span data-stu-id="13c4d-115">Requirements</span></span>  
 <span data-ttu-id="13c4d-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13c4d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c4d-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="13c4d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="13c4d-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="13c4d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c4d-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c4d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c4d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="13c4d-120">See Also</span></span>  
 [<span data-ttu-id="13c4d-121">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="13c4d-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="13c4d-122">裝載</span><span class="sxs-lookup"><span data-stu-id="13c4d-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
