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
ms.openlocfilehash: 15bdbc001838e3d13a9789c8f54daa80f3b6ef9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219820"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="02065-102">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="02065-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="02065-103">提供方法，檢查應用程式定義域的記憶體和 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="02065-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02065-104">方法</span><span class="sxs-lookup"><span data-stu-id="02065-104">Methods</span></span>  
  
|<span data-ttu-id="02065-105">方法</span><span class="sxs-lookup"><span data-stu-id="02065-105">Method</span></span>|<span data-ttu-id="02065-106">描述</span><span class="sxs-lookup"><span data-stu-id="02065-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02065-107">GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="02065-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="02065-108">取得以位元組為單位，因為它已建立，但不減去已回收的記憶體已建立的應用程式定義域的所有記憶體配置的大小總計。</span><span class="sxs-lookup"><span data-stu-id="02065-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="02065-109">GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="02065-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="02065-110">取得最後一個完整的封鎖記憶體回收回收的和目前的應用程式定義域所參考之位元組數目。</span><span class="sxs-lookup"><span data-stu-id="02065-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="02065-111">GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="02065-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="02065-112">取得已建立應用程式網域以來，在目前的應用程式網域中，執行時使用的所有執行緒的處理器總時間。</span><span class="sxs-lookup"><span data-stu-id="02065-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02065-113">備註</span><span class="sxs-lookup"><span data-stu-id="02065-113">Remarks</span></span>  
 <span data-ttu-id="02065-114">`ICLRAppDomainResourceMonitor`介面提供類似於下列的 managed 屬性的功能：</span><span class="sxs-lookup"><span data-stu-id="02065-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="02065-115">需求</span><span class="sxs-lookup"><span data-stu-id="02065-115">Requirements</span></span>  
 <span data-ttu-id="02065-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02065-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02065-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="02065-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="02065-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="02065-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="02065-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="02065-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02065-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02065-120">See also</span></span>

- [<span data-ttu-id="02065-121">\<appDomainResourceMonitoring > 項目</span><span class="sxs-lookup"><span data-stu-id="02065-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="02065-122">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="02065-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="02065-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="02065-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="02065-124">裝載</span><span class="sxs-lookup"><span data-stu-id="02065-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
