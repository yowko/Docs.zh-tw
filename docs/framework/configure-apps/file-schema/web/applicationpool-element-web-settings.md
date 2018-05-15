---
title: '&lt;應用程式集區&gt;項目 （Web 設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2eafc6b5ad1446fd07518f877a8ec001ad8dbd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltapplicationpoolgt-element-web-settings"></a><span data-ttu-id="7c77e-102">&lt;應用程式集區&gt;項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="7c77e-102">&lt;applicationPool&gt; Element (Web Settings)</span></span>
<span data-ttu-id="7c77e-103">指定用來管理整個處理序的行為，以整合模式上執行 ASP.NET 應用程式時由 ASP.NET 組態設定[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7c77e-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c77e-104">這個項目和功能它支援唯一的工作如果 ASP.NET 應用程式裝載於[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7c77e-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="7c77e-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7c77e-105">\<configuration></span></span>  
<span data-ttu-id="7c77e-106">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="7c77e-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="7c77e-107">\<應用程式集區 > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="7c77e-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c77e-108">語法</span><span class="sxs-lookup"><span data-stu-id="7c77e-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c77e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c77e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7c77e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7c77e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c77e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7c77e-111">Attributes</span></span>  
  
|<span data-ttu-id="7c77e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7c77e-112">Attribute</span></span>|<span data-ttu-id="7c77e-113">描述</span><span class="sxs-lookup"><span data-stu-id="7c77e-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="7c77e-114">指定 ASP.NET 允許每一 CPU 的同時要求數。</span><span class="sxs-lookup"><span data-stu-id="7c77e-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="7c77e-115">指定多少同時執行緒可以執行應用程式集區的每一個 CPU。</span><span class="sxs-lookup"><span data-stu-id="7c77e-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="7c77e-116">這會提供替代方法來控制 ASP.NET 的並行存取，因為您可以限制可用於每個 CPU 處理要求的 managed 執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="7c77e-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="7c77e-117">此設定預設值為 0，這表示，ASP.NET 不會限制每個 CPU，可以建立的執行緒數目雖然 CLR 執行緒集區也會限制可以建立的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="7c77e-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="7c77e-118">指定可以在單一處理序中加入佇列的 ASP.NET 的要求數目上限。</span><span class="sxs-lookup"><span data-stu-id="7c77e-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="7c77e-119">當兩個或多個 ASP.NET 應用程式執行單一應用程式集區中時，應用程式集區中的任何應用程式所提出之要求的累計集受限於這項設定。</span><span class="sxs-lookup"><span data-stu-id="7c77e-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c77e-120">子項目</span><span class="sxs-lookup"><span data-stu-id="7c77e-120">Child Elements</span></span>  
 <span data-ttu-id="7c77e-121">無。</span><span class="sxs-lookup"><span data-stu-id="7c77e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c77e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7c77e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7c77e-123">項目</span><span class="sxs-lookup"><span data-stu-id="7c77e-123">Element</span></span>|<span data-ttu-id="7c77e-124">描述</span><span class="sxs-lookup"><span data-stu-id="7c77e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c77e-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="7c77e-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="7c77e-126">包含 ASP.NET 裝載應用程式的互動方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7c77e-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c77e-127">備註</span><span class="sxs-lookup"><span data-stu-id="7c77e-127">Remarks</span></span>  
 <span data-ttu-id="7c77e-128">當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的時，這個項目組合可以可讓您設定 ASP.NET 如何管理執行緒和佇列的要求，當應用程式裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="7c77e-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="7c77e-129">如果您執行 IIS 6 或您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以傳統模式，或以 ISAPI 模式，會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="7c77e-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="7c77e-130">`applicationPool`設定會套用到特定的.NET framework 版本執行的所有應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="7c77e-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="7c77e-131">設定包含在 aspnet.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c77e-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="7c77e-132">沒有這個檔案針對 2.0 和.NET framework 4.0 版的版本。</span><span class="sxs-lookup"><span data-stu-id="7c77e-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="7c77e-133">（3.0 版和.NET framework 3.5 會共用 aspnet.config 檔案 2.0 版）。</span><span class="sxs-lookup"><span data-stu-id="7c77e-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c77e-134">如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]上[!INCLUDE[win7](../../../../../includes/win7-md.md)]，您可以設定每個應用程式集區的個別 aspnet.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c77e-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="7c77e-135">這可讓您調整對流程投入的每個應用程式集區執行緒的效能。</span><span class="sxs-lookup"><span data-stu-id="7c77e-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="7c77e-136">如`maxConcurrentRequestsPerCPU`，預設值為"5000 」 中設定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]有效地將關閉要求節流也就由 ASP.NET，除非您真的有 5000 個以上每一 CPU 的要求。</span><span class="sxs-lookup"><span data-stu-id="7c77e-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="7c77e-137">預設值改為取決於以自動管理每一 CPU 的並行存取 CLR 執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="7c77e-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="7c77e-138">應用程式，讓使用大量的非同步要求處理，或有多長時間執行要求被封鎖於網路 I/O，將受益於在增加的預設限制[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c77e-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="7c77e-139">設定`maxConcurrentRequestsPerCPU`為零會關閉使用的 managed 執行緒處理 ASP.NET 要求。</span><span class="sxs-lookup"><span data-stu-id="7c77e-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="7c77e-140">當應用程式 IIS 集區中，執行應用程式時，要求停留在 IIS I/O 執行緒，然後因此並行執行緒的 IIS 設定的。</span><span class="sxs-lookup"><span data-stu-id="7c77e-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="7c77e-141">`requestQueueLimit`設定的運作方式相同`requestQueueLimit`屬性[processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d)項目，它會設定 ASP.NET 應用程式的 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="7c77e-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="7c77e-142">不過， `requestQueueLimit` aspnet.config 檔案中的設定會覆寫`requestQueueLimit`Web.config 檔中設定。</span><span class="sxs-lookup"><span data-stu-id="7c77e-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="7c77e-143">換句話說，如果已設定這兩個屬性 （根據預設，這是 true）， `requestQueueLimit` aspnet.config 檔案中的設定的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7c77e-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c77e-144">範例</span><span class="sxs-lookup"><span data-stu-id="7c77e-144">Example</span></span>  
 <span data-ttu-id="7c77e-145">下列範例會示範如何在下列情況下 aspnet.config 檔案中設定 ASP.NET 整個處理序的行為：</span><span class="sxs-lookup"><span data-stu-id="7c77e-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
-   <span data-ttu-id="7c77e-146">應用程式裝載於[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="7c77e-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]<span data-ttu-id="7c77e-147"> 以整合模式執行。</span><span class="sxs-lookup"><span data-stu-id="7c77e-147"> is running in Integrated mode.</span></span>  
  
-   <span data-ttu-id="7c77e-148">應用程式使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7c77e-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="7c77e-149">此範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="7c77e-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="7c77e-150">項目資訊</span><span class="sxs-lookup"><span data-stu-id="7c77e-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c77e-151">命名空間</span><span class="sxs-lookup"><span data-stu-id="7c77e-151">Namespace</span></span>||  
|<span data-ttu-id="7c77e-152">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="7c77e-152">Schema Name</span></span>||  
|<span data-ttu-id="7c77e-153">驗證檔</span><span class="sxs-lookup"><span data-stu-id="7c77e-153">Validation File</span></span>||  
|<span data-ttu-id="7c77e-154">可以是空白</span><span class="sxs-lookup"><span data-stu-id="7c77e-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="7c77e-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c77e-155">See Also</span></span>  
 [<span data-ttu-id="7c77e-156">\<system.web> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="7c77e-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
