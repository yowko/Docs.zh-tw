---
title: ICLRAppDomainResourceMonitor 介面
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc2326c72c9a1c63c4740608e120ace5dc83ebee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434866"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="8d19e-102">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="8d19e-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="8d19e-103">提供方法，檢查應用程式定義域的記憶體和 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="8d19e-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d19e-104">方法</span><span class="sxs-lookup"><span data-stu-id="8d19e-104">Methods</span></span>  
  
|<span data-ttu-id="8d19e-105">方法</span><span class="sxs-lookup"><span data-stu-id="8d19e-105">Method</span></span>|<span data-ttu-id="8d19e-106">描述</span><span class="sxs-lookup"><span data-stu-id="8d19e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d19e-107">GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="8d19e-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="8d19e-108">取得以位元組為單位建立以來，但不減去已回收的記憶體，由應用程式定義域所做的所有記憶體配置的大小總計。</span><span class="sxs-lookup"><span data-stu-id="8d19e-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="8d19e-109">GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="8d19e-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="8d19e-110">取得的存活下來的最後一個完整的封鎖記憶體回收，且目前的應用程式定義域所參考之位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8d19e-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="8d19e-111">GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="8d19e-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="8d19e-112">取得後應用程式定義域建立以來，在目前的應用程式定義域中執行時用掉的所有執行緒的處理器總時間。</span><span class="sxs-lookup"><span data-stu-id="8d19e-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d19e-113">備註</span><span class="sxs-lookup"><span data-stu-id="8d19e-113">Remarks</span></span>  
 <span data-ttu-id="8d19e-114">`ICLRAppDomainResourceMonitor`介面提供的功能類似於受管理的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8d19e-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="8d19e-115">需求</span><span class="sxs-lookup"><span data-stu-id="8d19e-115">Requirements</span></span>  
 <span data-ttu-id="8d19e-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d19e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d19e-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8d19e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8d19e-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d19e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d19e-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d19e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d19e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d19e-120">See Also</span></span>  
 [<span data-ttu-id="8d19e-121">\<appDomainResourceMonitoring > 項目</span><span class="sxs-lookup"><span data-stu-id="8d19e-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="8d19e-122">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="8d19e-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="8d19e-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="8d19e-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="8d19e-124">裝載</span><span class="sxs-lookup"><span data-stu-id="8d19e-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
