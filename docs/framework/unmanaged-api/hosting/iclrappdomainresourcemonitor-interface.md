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
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674693"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="84066-102">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="84066-102">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="84066-103">提供可檢查應用程式域的記憶體和 CPU 使用量的方法。</span><span class="sxs-lookup"><span data-stu-id="84066-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84066-104">方法</span><span class="sxs-lookup"><span data-stu-id="84066-104">Methods</span></span>  
  
|<span data-ttu-id="84066-105">方法</span><span class="sxs-lookup"><span data-stu-id="84066-105">Method</span></span>|<span data-ttu-id="84066-106">描述</span><span class="sxs-lookup"><span data-stu-id="84066-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84066-107">GetCurrentAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="84066-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="84066-108">取得應用程式域自從建立之後所做的所有記憶體配置大小總計（以位元組為單位），而不會減去已進行垃圾收集的記憶體。</span><span class="sxs-lookup"><span data-stu-id="84066-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="84066-109">GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="84066-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="84066-110">取得最後一次完整、封鎖垃圾收集和目前應用程式域所參考的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="84066-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="84066-111">GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="84066-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="84066-112">取得在目前的應用程式域中執行時，在目前的應用程式域中執行之所有線程所使用的總處理器時間，因為已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="84066-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84066-113">備註</span><span class="sxs-lookup"><span data-stu-id="84066-113">Remarks</span></span>  

 <span data-ttu-id="84066-114">`ICLRAppDomainResourceMonitor`介面提供的功能類似下列受控屬性：</span><span class="sxs-lookup"><span data-stu-id="84066-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="84066-115">需求</span><span class="sxs-lookup"><span data-stu-id="84066-115">Requirements</span></span>  

 <span data-ttu-id="84066-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84066-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84066-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="84066-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="84066-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="84066-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84066-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84066-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84066-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84066-120">See also</span></span>

- [<span data-ttu-id="84066-121">\<appDomainResourceMonitoring> 元素</span><span class="sxs-lookup"><span data-stu-id="84066-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="84066-122">應用程式域資源監視</span><span class="sxs-lookup"><span data-stu-id="84066-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="84066-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="84066-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="84066-124">裝載</span><span class="sxs-lookup"><span data-stu-id="84066-124">Hosting</span></span>](index.md)
