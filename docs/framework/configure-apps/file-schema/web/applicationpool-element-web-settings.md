---
title: <applicationPool> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152850"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="59d1a-102">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="59d1a-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="59d1a-103">指定ASP.NET在 IIS 7.0 或更高版本中以整合模式運行ASP.NET應用程式時用於管理進程範圍行為的配置設置。</span><span class="sxs-lookup"><span data-stu-id="59d1a-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="59d1a-104">僅當ASP.NET應用程式託管在 IIS 7.0 或更高版本上時，此元素及其支援的功能才起作用。</span><span class="sxs-lookup"><span data-stu-id="59d1a-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="59d1a-105">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="59d1a-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="59d1a-106">&nbsp;&nbsp;[**\<系統.web>**](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="59d1a-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="59d1a-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式池>**</span><span class="sxs-lookup"><span data-stu-id="59d1a-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d1a-108">語法</span><span class="sxs-lookup"><span data-stu-id="59d1a-108">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59d1a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59d1a-109">Attributes and Elements</span></span>  

<span data-ttu-id="59d1a-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="59d1a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59d1a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="59d1a-111">Attributes</span></span>  
  
|<span data-ttu-id="59d1a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="59d1a-112">Attribute</span></span>|<span data-ttu-id="59d1a-113">描述</span><span class="sxs-lookup"><span data-stu-id="59d1a-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="59d1a-114">指定每個 CPU ASP.NET允許的同聲請求數。</span><span class="sxs-lookup"><span data-stu-id="59d1a-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="59d1a-115">指定每個 CPU 的應用程式池可以同時運行多少個執行緒。</span><span class="sxs-lookup"><span data-stu-id="59d1a-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="59d1a-116">這提供了一種控制ASP.NET併發的替代方法，因為您可以限制每個 CPU 可用於服務請求的託管執行緒數。</span><span class="sxs-lookup"><span data-stu-id="59d1a-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="59d1a-117">預設情況下，此設置為 0，這意味著ASP.NET不會限制每個 CPU 可以創建的執行緒數，儘管 CLR 執行緒池也限制可創建的執行緒數。</span><span class="sxs-lookup"><span data-stu-id="59d1a-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="59d1a-118">指定可在單個進程中排隊等待ASP.NET的最大請求數。</span><span class="sxs-lookup"><span data-stu-id="59d1a-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="59d1a-119">當兩個或兩個ASP.NET多個應用程式在單個應用程式池中運行時，向應用程式池中的任何應用程式發出的請求的累積集受此設置的約束。</span><span class="sxs-lookup"><span data-stu-id="59d1a-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59d1a-120">子元素</span><span class="sxs-lookup"><span data-stu-id="59d1a-120">Child Elements</span></span>  
 <span data-ttu-id="59d1a-121">無。</span><span class="sxs-lookup"><span data-stu-id="59d1a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59d1a-122">父項目</span><span class="sxs-lookup"><span data-stu-id="59d1a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="59d1a-123">元素</span><span class="sxs-lookup"><span data-stu-id="59d1a-123">Element</span></span>|<span data-ttu-id="59d1a-124">描述</span><span class="sxs-lookup"><span data-stu-id="59d1a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d1a-125">\<系統.web></span><span class="sxs-lookup"><span data-stu-id="59d1a-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="59d1a-126">包含有關ASP.NET如何與主機應用程式交互的資訊。</span><span class="sxs-lookup"><span data-stu-id="59d1a-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d1a-127">備註</span><span class="sxs-lookup"><span data-stu-id="59d1a-127">Remarks</span></span>  

<span data-ttu-id="59d1a-128">在整合模式下運行 IIS 7.0 或更高版本時，此元素組合允許您配置在應用程式託管在 IIS 應用程式池中時ASP.NET如何管理執行緒和佇列請求。</span><span class="sxs-lookup"><span data-stu-id="59d1a-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="59d1a-129">如果您運行 IIS 6 或在傳統模式或 ISAPI 模式下運行 IIS 7.0，則忽略這些設置。</span><span class="sxs-lookup"><span data-stu-id="59d1a-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="59d1a-130">這些`applicationPool`設置適用于在 .NET 框架的特定版本上運行的所有應用程式池。</span><span class="sxs-lookup"><span data-stu-id="59d1a-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="59d1a-131">這些設置包含在 aspnet.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="59d1a-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="59d1a-132">對於 .NET Framework 的版本 2.0 和 4.0，有此檔的版本。</span><span class="sxs-lookup"><span data-stu-id="59d1a-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="59d1a-133">（.NET 框架的版本 3.0 和 3.5 與版本 2.0 共用 aspnet.config 檔。</span><span class="sxs-lookup"><span data-stu-id="59d1a-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="59d1a-134">如果在 Windows 7 上運行 IIS 7.0，則可以為每個應用程式池配置單獨的 aspnet.config 檔。</span><span class="sxs-lookup"><span data-stu-id="59d1a-134">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="59d1a-135">這允許您為每個應用程式池定制執行緒的性能。</span><span class="sxs-lookup"><span data-stu-id="59d1a-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="59d1a-136">對於`maxConcurrentRequestsPerCPU`此設置，.NET Framework 4 中的預設設置"5000"可有效關閉由ASP.NET控制的請求限制，除非您每個 CPU 實際上有 5000 個或更多的請求。</span><span class="sxs-lookup"><span data-stu-id="59d1a-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="59d1a-137">預設設置取決於 CLR 執行緒池，以自動管理每個 CPU 的併發性。</span><span class="sxs-lookup"><span data-stu-id="59d1a-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="59d1a-138">大量使用非同步請求處理或網路 I/O 上有許多長時間運行的請求的應用程式將受益于 .NET 框架 4 中增加的預設限制。</span><span class="sxs-lookup"><span data-stu-id="59d1a-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="59d1a-139">設置為`maxConcurrentRequestsPerCPU`零將關閉使用託管執行緒來處理ASP.NET請求。</span><span class="sxs-lookup"><span data-stu-id="59d1a-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="59d1a-140">當應用程式在 IIS 應用程式池中運行時，請求將停留在 IIS I/O 執行緒上，因此 IIS 執行緒設置會限制併發。</span><span class="sxs-lookup"><span data-stu-id="59d1a-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="59d1a-141">該`requestQueueLimit`設置的工作方式與[processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) `requestQueueLimit`元素的屬性相同，該屬性在 Web.config 檔中設置為ASP.NET應用程式。</span><span class="sxs-lookup"><span data-stu-id="59d1a-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="59d1a-142">但是，aspnet.config`requestQueueLimit`檔中的設置將覆蓋 Web.config 檔中的`requestQueueLimit`設置。</span><span class="sxs-lookup"><span data-stu-id="59d1a-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="59d1a-143">換句話說，如果兩個屬性都設置了（預設情況下，這是 true），則`requestQueueLimit`aspnet.config 檔中的設置優先。</span><span class="sxs-lookup"><span data-stu-id="59d1a-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59d1a-144">範例</span><span class="sxs-lookup"><span data-stu-id="59d1a-144">Example</span></span>  

<span data-ttu-id="59d1a-145">下面的示例演示如何在以下情況下配置 aspnet.config 檔中ASP.NET進程範圍的行為：</span><span class="sxs-lookup"><span data-stu-id="59d1a-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="59d1a-146">應用程式託管在 IIS 7.0 應用程式池中。</span><span class="sxs-lookup"><span data-stu-id="59d1a-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="59d1a-147">IIS 7.0 以整合模式運行。</span><span class="sxs-lookup"><span data-stu-id="59d1a-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="59d1a-148">應用程式正在使用 .NET 框架 3.5 SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="59d1a-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="59d1a-149">示例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="59d1a-149">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="59d1a-150">項目資訊</span><span class="sxs-lookup"><span data-stu-id="59d1a-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59d1a-151">命名空間</span><span class="sxs-lookup"><span data-stu-id="59d1a-151">Namespace</span></span>||  
|<span data-ttu-id="59d1a-152">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="59d1a-152">Schema Name</span></span>||  
|<span data-ttu-id="59d1a-153">驗證檔</span><span class="sxs-lookup"><span data-stu-id="59d1a-153">Validation File</span></span>||  
|<span data-ttu-id="59d1a-154">可以為空</span><span class="sxs-lookup"><span data-stu-id="59d1a-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="59d1a-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59d1a-155">See also</span></span>

- [<span data-ttu-id="59d1a-156">\<系統.web>元素（Web 設置）</span><span class="sxs-lookup"><span data-stu-id="59d1a-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
