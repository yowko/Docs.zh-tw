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
ms.openlocfilehash: 7d02478c2421823ce2acb533d2abea2ea8b13c74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950282"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="1b23c-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="1b23c-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="1b23c-103">取得應用程式域自建立後所建立之所有記憶體配置的總大小 (以位元組為單位), 而不會減去已進行垃圾收集的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1b23c-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b23c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b23c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b23c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b23c-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="1b23c-106">在要求之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b23c-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="1b23c-107">脫銷所有記憶體配置的總大小指標。</span><span class="sxs-lookup"><span data-stu-id="1b23c-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b23c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b23c-108">Return Value</span></span>  
 <span data-ttu-id="1b23c-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b23c-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1b23c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b23c-110">HRESULT</span></span>|<span data-ttu-id="1b23c-111">描述</span><span class="sxs-lookup"><span data-stu-id="1b23c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b23c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b23c-112">S_OK</span></span>|<span data-ttu-id="1b23c-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1b23c-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1b23c-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="1b23c-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="1b23c-115">應用程式域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="1b23c-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b23c-116">備註</span><span class="sxs-lookup"><span data-stu-id="1b23c-116">Remarks</span></span>  
 <span data-ttu-id="1b23c-117">這個方法是 managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>屬性的不受管理對等。</span><span class="sxs-lookup"><span data-stu-id="1b23c-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b23c-118">需求</span><span class="sxs-lookup"><span data-stu-id="1b23c-118">Requirements</span></span>  
 <span data-ttu-id="1b23c-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b23c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b23c-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1b23c-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1b23c-121">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b23c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b23c-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b23c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b23c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b23c-123">See also</span></span>

- [<span data-ttu-id="1b23c-124">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="1b23c-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="1b23c-125">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="1b23c-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1b23c-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1b23c-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1b23c-127">裝載</span><span class="sxs-lookup"><span data-stu-id="1b23c-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
