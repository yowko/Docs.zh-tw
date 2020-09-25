---
title: <applicationPool> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 963b25e57ae8c2cc59dcc3e50ae2a52cc04f54a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185635"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="38a42-102">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="38a42-102">\<applicationPool> Element (Web Settings)</span></span>

<span data-ttu-id="38a42-103">指定當 ASP.NET 應用程式在 IIS 7.0 或更新版本上以整合模式執行時，ASP.NET 用來管理整個進程行為的設定。</span><span class="sxs-lookup"><span data-stu-id="38a42-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38a42-104">只有當您的 ASP.NET 應用程式裝載于 IIS 7.0 或更新版本時，此專案和它所支援的功能才會運作。</span><span class="sxs-lookup"><span data-stu-id="38a42-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="38a42-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38a42-105">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38a42-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38a42-106">Attributes and Elements</span></span>  

<span data-ttu-id="38a42-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="38a42-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38a42-108">屬性</span><span class="sxs-lookup"><span data-stu-id="38a42-108">Attributes</span></span>  
  
|<span data-ttu-id="38a42-109">屬性</span><span class="sxs-lookup"><span data-stu-id="38a42-109">Attribute</span></span>|<span data-ttu-id="38a42-110">描述</span><span class="sxs-lookup"><span data-stu-id="38a42-110">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="38a42-111">指定 ASP.NET 允許每個 CPU 的同時要求數。</span><span class="sxs-lookup"><span data-stu-id="38a42-111">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="38a42-112">指定每個 CPU 的應用程式集區可以同時執行的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="38a42-112">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="38a42-113">這提供了控制 ASP.NET 並行的另一種方式，因為您可以限制每個 CPU 可以用來處理要求的 managed 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="38a42-113">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="38a42-114">依預設，此設定為0，這表示 ASP.NET 不會限制每個 CPU 可以建立的執行緒數目，但 CLR 執行緒集區也會限制可以建立的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="38a42-114">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="38a42-115">指定可在單一進程中將 ASP.NET 排入佇列的要求數目上限。</span><span class="sxs-lookup"><span data-stu-id="38a42-115">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="38a42-116">當兩個或多個 ASP.NET 應用程式在單一應用程式集區中執行時，對應用程式集區中的任何應用程式進行的累計要求集會受限於這項設定。</span><span class="sxs-lookup"><span data-stu-id="38a42-116">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38a42-117">子元素</span><span class="sxs-lookup"><span data-stu-id="38a42-117">Child Elements</span></span>  

 <span data-ttu-id="38a42-118">無。</span><span class="sxs-lookup"><span data-stu-id="38a42-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38a42-119">父項目</span><span class="sxs-lookup"><span data-stu-id="38a42-119">Parent Elements</span></span>  
  
|<span data-ttu-id="38a42-120">項目</span><span class="sxs-lookup"><span data-stu-id="38a42-120">Element</span></span>|<span data-ttu-id="38a42-121">描述</span><span class="sxs-lookup"><span data-stu-id="38a42-121">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="38a42-122">包含 ASP.NET 如何與主應用程式互動的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="38a42-122">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38a42-123">備註</span><span class="sxs-lookup"><span data-stu-id="38a42-123">Remarks</span></span>  

<span data-ttu-id="38a42-124">當您在整合模式中執行 IIS 7.0 或更新版本時，此元素組合可讓您設定當應用程式裝載于 IIS 應用程式集區時，ASP.NET 管理執行緒和佇列要求的方式。</span><span class="sxs-lookup"><span data-stu-id="38a42-124">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="38a42-125">如果您執行的是 IIS 6，或是以傳統模式或在 ISAPI 模式中執行 IIS 7.0，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="38a42-125">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="38a42-126">這些 `applicationPool` 設定會套用至在特定版本的 .NET Framework 上執行的所有應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="38a42-126">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="38a42-127">這些設定包含在 aspnet.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="38a42-127">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="38a42-128">此檔案的版本為2.0 和4.0 版的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="38a42-128">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="38a42-129">.NET Framework 的 (版本3.0 和3.5 會共用版本為2.0 的 aspnet.config 檔案 ) </span><span class="sxs-lookup"><span data-stu-id="38a42-129">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38a42-130">如果您在 Windows 7 上執行 IIS 7.0，您可以為每個應用程式集區設定個別的 aspnet.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="38a42-130">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="38a42-131">這可讓您針對每個應用程式集區量身打造執行緒的效能。</span><span class="sxs-lookup"><span data-stu-id="38a42-131">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="38a42-132">針對此 `maxConcurrentRequestsPerCPU` 設定，.NET Framework 4 中 "5000" 的預設設定會有效地關閉由 ASP.NET 控制的要求節流，除非您實際上有每個 CPU 的5000或更多要求。</span><span class="sxs-lookup"><span data-stu-id="38a42-132">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="38a42-133">預設設定會改為依賴 CLR 執行緒集區，以自動管理每個 CPU 的並行。</span><span class="sxs-lookup"><span data-stu-id="38a42-133">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="38a42-134">大量使用非同步要求處理的應用程式，或在網路 i/o 上封鎖許多長時間執行要求的應用程式，將會受益于 .NET Framework 4 中增加的預設限制。</span><span class="sxs-lookup"><span data-stu-id="38a42-134">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="38a42-135">將設定 `maxConcurrentRequestsPerCPU` 為零會關閉使用 managed 執行緒 ASP.NET 要求。</span><span class="sxs-lookup"><span data-stu-id="38a42-135">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="38a42-136">當應用程式在 IIS 應用程式集區中執行時，要求會保留在 IIS i/o 執行緒上，因此會由 IIS 執行緒設定來節流平行存取。</span><span class="sxs-lookup"><span data-stu-id="38a42-136">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="38a42-137">`requestQueueLimit`設定的運作方式與 processModel 專案的 `requestQueueLimit` 屬性相同， [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))它是在 ASP.NET 應用程式的 Web.config 檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="38a42-137">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="38a42-138">不過， `requestQueueLimit` aspnet.config 檔案中的設定會覆寫 `requestQueueLimit` Web.config 檔案中的設定。</span><span class="sxs-lookup"><span data-stu-id="38a42-138">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="38a42-139">換句話說，如果兩個屬性都設定 (預設為) ，則 `requestQueueLimit` aspnet.config 檔中的設定優先。</span><span class="sxs-lookup"><span data-stu-id="38a42-139">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38a42-140">範例</span><span class="sxs-lookup"><span data-stu-id="38a42-140">Example</span></span>  

<span data-ttu-id="38a42-141">下列範例示範如何在下列情況下，在 aspnet.config 檔案中設定 ASP.NET 全進程的行為：</span><span class="sxs-lookup"><span data-stu-id="38a42-141">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="38a42-142">應用程式裝載于 IIS 7.0 應用程式集區中。</span><span class="sxs-lookup"><span data-stu-id="38a42-142">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="38a42-143">IIS 7.0 以整合模式執行。</span><span class="sxs-lookup"><span data-stu-id="38a42-143">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="38a42-144">應用程式使用 .NET Framework 3.5 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="38a42-144">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="38a42-145">範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="38a42-145">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="38a42-146">項目資訊</span><span class="sxs-lookup"><span data-stu-id="38a42-146">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38a42-147">命名空間</span><span class="sxs-lookup"><span data-stu-id="38a42-147">Namespace</span></span>||  
|<span data-ttu-id="38a42-148">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="38a42-148">Schema Name</span></span>||  
|<span data-ttu-id="38a42-149">驗證檔</span><span class="sxs-lookup"><span data-stu-id="38a42-149">Validation File</span></span>||  
|<span data-ttu-id="38a42-150">可以是空的</span><span class="sxs-lookup"><span data-stu-id="38a42-150">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="38a42-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a42-151">See also</span></span>

- [<span data-ttu-id="38a42-152">\<system.web> (Web 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="38a42-152">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
