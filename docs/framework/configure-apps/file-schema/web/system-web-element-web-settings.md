---
title: <system.web> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 50566422c5e28585e93171c991144cf12a6866eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131946"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="dd4aa-102">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="dd4aa-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="dd4aa-103">包含 ASP.NET 裝載層管理整個處理序行為的方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="dd4aa-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dd4aa-104">\<configuration></span></span>  
<span data-ttu-id="dd4aa-105">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="dd4aa-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4aa-106">語法</span><span class="sxs-lookup"><span data-stu-id="dd4aa-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd4aa-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd4aa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dd4aa-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd4aa-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dd4aa-109">Attributes</span></span>  
 <span data-ttu-id="dd4aa-110">無。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd4aa-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dd4aa-111">Child Elements</span></span>  
  
|<span data-ttu-id="dd4aa-112">項目</span><span class="sxs-lookup"><span data-stu-id="dd4aa-112">Element</span></span>|<span data-ttu-id="dd4aa-113">描述</span><span class="sxs-lookup"><span data-stu-id="dd4aa-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd4aa-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="dd4aa-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="dd4aa-115">指定在 aspnet.config 檔中的 IIS 應用程式集區的組態設定。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd4aa-116">父項目</span><span class="sxs-lookup"><span data-stu-id="dd4aa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dd4aa-117">項目</span><span class="sxs-lookup"><span data-stu-id="dd4aa-117">Element</span></span>|<span data-ttu-id="dd4aa-118">描述</span><span class="sxs-lookup"><span data-stu-id="dd4aa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd4aa-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dd4aa-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="dd4aa-120">指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd4aa-121">備註</span><span class="sxs-lookup"><span data-stu-id="dd4aa-121">Remarks</span></span>  
 <span data-ttu-id="dd4aa-122">`system.web`項目和其子系`applicationPool`項目已新增至[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]自[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="dd4aa-123">當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，此項目組合，可讓您設定 ASP.NET 如何管理執行緒，以及如何它排入佇列的要求 ASP.NET 裝載在 IIS 應用程式集區時。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="dd4aa-124">如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統或 ISAPI 模式中，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd4aa-125">範例</span><span class="sxs-lookup"><span data-stu-id="dd4aa-125">Example</span></span>  
 <span data-ttu-id="dd4aa-126">下列範例示範如何在 aspnet.config 檔中設定 ASP.NET 全處理序行為，當 ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="dd4aa-127">此範例假設 IIS 正在執行中整合式驗證模式和應用程式使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="dd4aa-128">此行為的版本中不會發生[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]早於[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="dd4aa-129">在範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="dd4aa-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="dd4aa-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="dd4aa-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd4aa-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="dd4aa-131">Namespace</span></span>||  
|<span data-ttu-id="dd4aa-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="dd4aa-132">Schema Name</span></span>||  
|<span data-ttu-id="dd4aa-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="dd4aa-133">Validation File</span></span>||  
|<span data-ttu-id="dd4aa-134">可以是空白</span><span class="sxs-lookup"><span data-stu-id="dd4aa-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="dd4aa-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd4aa-135">See also</span></span>

- [<span data-ttu-id="dd4aa-136">\<applicationPool > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="dd4aa-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
