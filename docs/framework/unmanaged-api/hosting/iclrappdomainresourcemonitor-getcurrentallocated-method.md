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
ms.openlocfilehash: 4011881e98c109458bf87efcc1b09463c064f23f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431951"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="c4c23-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="c4c23-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="c4c23-103">取得以位元組為單位建立以來，但不減去已回收的記憶體，由應用程式定義域所做的所有記憶體配置的大小總計。</span><span class="sxs-lookup"><span data-stu-id="c4c23-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c23-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4c23-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4c23-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4c23-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="c4c23-106">[in]要求的應用程式定義域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c4c23-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="c4c23-107">[out]所有記憶體配置總大小的指標。</span><span class="sxs-lookup"><span data-stu-id="c4c23-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4c23-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4c23-108">Return Value</span></span>  
 <span data-ttu-id="c4c23-109">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4c23-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c4c23-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4c23-110">HRESULT</span></span>|<span data-ttu-id="c4c23-111">描述</span><span class="sxs-lookup"><span data-stu-id="c4c23-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4c23-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4c23-112">S_OK</span></span>|<span data-ttu-id="c4c23-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c4c23-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c4c23-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="c4c23-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="c4c23-115">應用程式定義域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="c4c23-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4c23-116">備註</span><span class="sxs-lookup"><span data-stu-id="c4c23-116">Remarks</span></span>  
 <span data-ttu-id="c4c23-117">這個方法相當於 unmanaged 的 managed<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="c4c23-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c23-118">需求</span><span class="sxs-lookup"><span data-stu-id="c4c23-118">Requirements</span></span>  
 <span data-ttu-id="c4c23-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c23-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c23-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c4c23-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c4c23-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4c23-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4c23-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c23-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c23-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c23-123">See Also</span></span>  
 [<span data-ttu-id="c4c23-124">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="c4c23-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="c4c23-125">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="c4c23-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="c4c23-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c4c23-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c4c23-127">裝載</span><span class="sxs-lookup"><span data-stu-id="c4c23-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
