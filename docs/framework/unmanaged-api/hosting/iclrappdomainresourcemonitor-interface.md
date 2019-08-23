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
ms.openlocfilehash: 597381c8ab31e86a02f870a24f165676d200b66e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965019"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="384fa-102">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="384fa-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="384fa-103">提供可檢查應用程式域記憶體和 CPU 使用量的方法。</span><span class="sxs-lookup"><span data-stu-id="384fa-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="384fa-104">方法</span><span class="sxs-lookup"><span data-stu-id="384fa-104">Methods</span></span>  
  
|<span data-ttu-id="384fa-105">方法</span><span class="sxs-lookup"><span data-stu-id="384fa-105">Method</span></span>|<span data-ttu-id="384fa-106">說明</span><span class="sxs-lookup"><span data-stu-id="384fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="384fa-107">GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="384fa-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="384fa-108">取得應用程式域自建立後所建立之所有記憶體配置的總大小 (以位元組為單位), 而不會減去已進行垃圾收集的記憶體。</span><span class="sxs-lookup"><span data-stu-id="384fa-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="384fa-109">GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="384fa-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="384fa-110">取得最後一次完整、封鎖垃圾收集以及目前應用程式域所參考的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="384fa-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="384fa-111">GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="384fa-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="384fa-112">取得自應用程式域建立後, 所有線程在目前應用程式域中執行時所使用的處理器時間總計。</span><span class="sxs-lookup"><span data-stu-id="384fa-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="384fa-113">備註</span><span class="sxs-lookup"><span data-stu-id="384fa-113">Remarks</span></span>  
 <span data-ttu-id="384fa-114">`ICLRAppDomainResourceMonitor`介面會提供類似下列受控屬性的功能:</span><span class="sxs-lookup"><span data-stu-id="384fa-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="384fa-115">需求</span><span class="sxs-lookup"><span data-stu-id="384fa-115">Requirements</span></span>  
 <span data-ttu-id="384fa-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="384fa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384fa-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="384fa-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="384fa-118">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="384fa-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="384fa-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="384fa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384fa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384fa-120">See also</span></span>

- [<span data-ttu-id="384fa-121">\<appDomainResourceMonitoring > 元素</span><span class="sxs-lookup"><span data-stu-id="384fa-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="384fa-122">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="384fa-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="384fa-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="384fa-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="384fa-124">裝載</span><span class="sxs-lookup"><span data-stu-id="384fa-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
