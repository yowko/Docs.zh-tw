---
title: '&lt;system.web&gt;項目 （Web 設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7527ee9e7528a0da47529bae93e8112705e03a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="56fbb-102">&lt;system.web&gt;項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="56fbb-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="56fbb-103">包含 ASP.NET 裝載層如何管理整個處理序行為的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56fbb-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="56fbb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="56fbb-104">\<configuration></span></span>  
<span data-ttu-id="56fbb-105">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="56fbb-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fbb-106">語法</span><span class="sxs-lookup"><span data-stu-id="56fbb-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56fbb-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56fbb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="56fbb-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56fbb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56fbb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="56fbb-109">Attributes</span></span>  
 <span data-ttu-id="56fbb-110">無。</span><span class="sxs-lookup"><span data-stu-id="56fbb-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56fbb-111">子項目</span><span class="sxs-lookup"><span data-stu-id="56fbb-111">Child Elements</span></span>  
  
|<span data-ttu-id="56fbb-112">項目</span><span class="sxs-lookup"><span data-stu-id="56fbb-112">Element</span></span>|<span data-ttu-id="56fbb-113">描述</span><span class="sxs-lookup"><span data-stu-id="56fbb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56fbb-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="56fbb-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="56fbb-115">指定 aspnet.config 檔案中的 IIS 應用程式集區的組態設定。</span><span class="sxs-lookup"><span data-stu-id="56fbb-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56fbb-116">父項目</span><span class="sxs-lookup"><span data-stu-id="56fbb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="56fbb-117">項目</span><span class="sxs-lookup"><span data-stu-id="56fbb-117">Element</span></span>|<span data-ttu-id="56fbb-118">描述</span><span class="sxs-lookup"><span data-stu-id="56fbb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56fbb-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="56fbb-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="56fbb-120">指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="56fbb-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56fbb-121">備註</span><span class="sxs-lookup"><span data-stu-id="56fbb-121">Remarks</span></span>  
 <span data-ttu-id="56fbb-122">`system.web`項目和其子系`applicationPool`項目已加入至[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]從[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56fbb-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="56fbb-123">當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，這個項目組合可以可讓您設定 ASP.NET 如何管理執行緒，以及如何它要求加入佇列時，ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="56fbb-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="56fbb-124">如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統 」 或 「 ISAPI 模式中，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="56fbb-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56fbb-125">範例</span><span class="sxs-lookup"><span data-stu-id="56fbb-125">Example</span></span>  
 <span data-ttu-id="56fbb-126">下列範例會示範如何設定 ASP.NET 整個處理序行為 aspnet.config 檔案中，當 ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="56fbb-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="56fbb-127">這個範例假設 IIS 正在執行到整合式模式和應用程式正在使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="56fbb-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="56fbb-128">版本中不會發生這種行為[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]早於[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56fbb-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="56fbb-129">此範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="56fbb-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="56fbb-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="56fbb-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56fbb-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="56fbb-131">Namespace</span></span>||  
|<span data-ttu-id="56fbb-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="56fbb-132">Schema Name</span></span>||  
|<span data-ttu-id="56fbb-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="56fbb-133">Validation File</span></span>||  
|<span data-ttu-id="56fbb-134">可以是空白</span><span class="sxs-lookup"><span data-stu-id="56fbb-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="56fbb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56fbb-135">See Also</span></span>  
 [<span data-ttu-id="56fbb-136">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="56fbb-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
