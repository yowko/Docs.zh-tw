---
title: ICLRMetaHost::EnumerateInstalledRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09931dce7afdb7944cf9912b5146e44fda131935
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173403"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="a3bb3-102">ICLRMetaHost::EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="a3bb3-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="a3bb3-103">傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個版本的 common language runtime (CLR) 安裝在電腦上的介面。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3bb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3bb3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3bb3-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3bb3-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="a3bb3-106">[out]列舉型別[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面對應至每個版本的電腦已安裝的 CLR。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3bb3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3bb3-107">Return Value</span></span>  
 <span data-ttu-id="a3bb3-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a3bb3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3bb3-109">HRESULT</span></span>|<span data-ttu-id="a3bb3-110">描述</span><span class="sxs-lookup"><span data-stu-id="a3bb3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3bb3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3bb3-111">S_OK</span></span>|<span data-ttu-id="a3bb3-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="a3bb3-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a3bb3-113">E_POINTER</span></span>|<span data-ttu-id="a3bb3-114">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3bb3-115">需求</span><span class="sxs-lookup"><span data-stu-id="a3bb3-115">Requirements</span></span>  
 <span data-ttu-id="a3bb3-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3bb3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3bb3-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a3bb3-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3bb3-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3bb3-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3bb3-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3bb3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3bb3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3bb3-120">See also</span></span>

- [<span data-ttu-id="a3bb3-121">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="a3bb3-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="a3bb3-122">裝載</span><span class="sxs-lookup"><span data-stu-id="a3bb3-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
