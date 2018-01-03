---
title: "&lt;system.web&gt;項目 （Web 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="d784f-102">&lt;system.web&gt;項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="d784f-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="d784f-103">包含 ASP.NET 裝載層如何管理整個處理序行為的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d784f-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="d784f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d784f-104">\<configuration></span></span>  
<span data-ttu-id="d784f-105">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="d784f-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d784f-106">語法</span><span class="sxs-lookup"><span data-stu-id="d784f-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d784f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d784f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d784f-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d784f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d784f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d784f-109">Attributes</span></span>  
 <span data-ttu-id="d784f-110">無。</span><span class="sxs-lookup"><span data-stu-id="d784f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d784f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d784f-111">Child Elements</span></span>  
  
|<span data-ttu-id="d784f-112">項目</span><span class="sxs-lookup"><span data-stu-id="d784f-112">Element</span></span>|<span data-ttu-id="d784f-113">描述</span><span class="sxs-lookup"><span data-stu-id="d784f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d784f-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="d784f-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="d784f-115">指定 aspnet.config 檔案中的 IIS 應用程式集區的組態設定。</span><span class="sxs-lookup"><span data-stu-id="d784f-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d784f-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d784f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d784f-117">項目</span><span class="sxs-lookup"><span data-stu-id="d784f-117">Element</span></span>|<span data-ttu-id="d784f-118">描述</span><span class="sxs-lookup"><span data-stu-id="d784f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d784f-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d784f-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d784f-120">指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d784f-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d784f-121">備註</span><span class="sxs-lookup"><span data-stu-id="d784f-121">Remarks</span></span>  
 <span data-ttu-id="d784f-122">`system.web`項目和其子系`applicationPool`項目已加入至[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]從[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d784f-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="d784f-123">當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，這個項目組合可以可讓您設定 ASP.NET 如何管理執行緒，以及如何它要求加入佇列時，ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="d784f-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="d784f-124">如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統 」 或 「 ISAPI 模式中，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="d784f-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d784f-125">範例</span><span class="sxs-lookup"><span data-stu-id="d784f-125">Example</span></span>  
 <span data-ttu-id="d784f-126">下列範例會示範如何設定 ASP.NET 整個處理序行為 aspnet.config 檔案中，當 ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="d784f-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="d784f-127">這個範例假設 IIS 正在執行到整合式模式和應用程式正在使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d784f-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="d784f-128">版本中不會發生這種行為[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]早於[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d784f-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="d784f-129">此範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="d784f-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="d784f-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="d784f-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d784f-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="d784f-131">Namespace</span></span>||  
|<span data-ttu-id="d784f-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="d784f-132">Schema Name</span></span>||  
|<span data-ttu-id="d784f-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="d784f-133">Validation File</span></span>||  
|<span data-ttu-id="d784f-134">可以是空白</span><span class="sxs-lookup"><span data-stu-id="d784f-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d784f-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="d784f-135">See Also</span></span>  
 [<span data-ttu-id="d784f-136">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="d784f-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
