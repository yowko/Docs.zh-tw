---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97b00ff01125e000dec7840f122ed0c69ec9878f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502524"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="525dc-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="525dc-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="525dc-103">取得以位元組為單位，因為它已建立，但不減去已回收的記憶體已建立的應用程式定義域的所有記憶體配置的大小總計。</span><span class="sxs-lookup"><span data-stu-id="525dc-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="525dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="525dc-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="525dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="525dc-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="525dc-106">[in]要求的應用程式定義域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="525dc-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="525dc-107">[out]所有記憶體配置的總大小指標。</span><span class="sxs-lookup"><span data-stu-id="525dc-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="525dc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="525dc-108">Return Value</span></span>  
 <span data-ttu-id="525dc-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="525dc-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="525dc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="525dc-110">HRESULT</span></span>|<span data-ttu-id="525dc-111">描述</span><span class="sxs-lookup"><span data-stu-id="525dc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="525dc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="525dc-112">S_OK</span></span>|<span data-ttu-id="525dc-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="525dc-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="525dc-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="525dc-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="525dc-115">應用程式定義域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="525dc-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="525dc-116">備註</span><span class="sxs-lookup"><span data-stu-id="525dc-116">Remarks</span></span>  
 <span data-ttu-id="525dc-117">這個方法相當於未受管理的受管理<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="525dc-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="525dc-118">需求</span><span class="sxs-lookup"><span data-stu-id="525dc-118">Requirements</span></span>  
 <span data-ttu-id="525dc-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="525dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="525dc-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="525dc-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="525dc-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="525dc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="525dc-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="525dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="525dc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="525dc-123">See also</span></span>
- [<span data-ttu-id="525dc-124">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="525dc-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="525dc-125">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="525dc-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="525dc-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="525dc-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="525dc-127">裝載</span><span class="sxs-lookup"><span data-stu-id="525dc-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
