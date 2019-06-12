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
ms.openlocfilehash: 687398e47ad95e3234c29571eeeac0c9d2d83a39
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832780"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="3edc3-102">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="3edc3-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="3edc3-103">包含 ASP.NET 裝載層管理整個處理序行為的方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3edc3-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="3edc3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3edc3-104">\<configuration></span></span>  
<span data-ttu-id="3edc3-105">\<system.web > 項目 （Web 設定）</span><span class="sxs-lookup"><span data-stu-id="3edc3-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3edc3-106">語法</span><span class="sxs-lookup"><span data-stu-id="3edc3-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3edc3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3edc3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3edc3-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3edc3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3edc3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3edc3-109">Attributes</span></span>  
 <span data-ttu-id="3edc3-110">無。</span><span class="sxs-lookup"><span data-stu-id="3edc3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3edc3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3edc3-111">Child Elements</span></span>  
  
|<span data-ttu-id="3edc3-112">項目</span><span class="sxs-lookup"><span data-stu-id="3edc3-112">Element</span></span>|<span data-ttu-id="3edc3-113">描述</span><span class="sxs-lookup"><span data-stu-id="3edc3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3edc3-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="3edc3-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="3edc3-115">指定在 aspnet.config 檔中的 IIS 應用程式集區的組態設定。</span><span class="sxs-lookup"><span data-stu-id="3edc3-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3edc3-116">父項目</span><span class="sxs-lookup"><span data-stu-id="3edc3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3edc3-117">項目</span><span class="sxs-lookup"><span data-stu-id="3edc3-117">Element</span></span>|<span data-ttu-id="3edc3-118">描述</span><span class="sxs-lookup"><span data-stu-id="3edc3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3edc3-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3edc3-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="3edc3-120">所有由 common language runtime 和.NET Framework 應用程式的組態檔中指定的根項目。</span><span class="sxs-lookup"><span data-stu-id="3edc3-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3edc3-121">備註</span><span class="sxs-lookup"><span data-stu-id="3edc3-121">Remarks</span></span>  
 <span data-ttu-id="3edc3-122">`system.web`項目和其子系`applicationPool`元素已新增至.NET Framework，.NET Framework 3.5 sp1。</span><span class="sxs-lookup"><span data-stu-id="3edc3-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="3edc3-123">當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，此項目組合，可讓您設定 ASP.NET 如何管理執行緒，以及如何它排入佇列的要求 ASP.NET 裝載在 IIS 應用程式集區時。</span><span class="sxs-lookup"><span data-stu-id="3edc3-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="3edc3-124">如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統或 ISAPI 模式中，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="3edc3-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3edc3-125">範例</span><span class="sxs-lookup"><span data-stu-id="3edc3-125">Example</span></span>  
 <span data-ttu-id="3edc3-126">下列範例示範如何在 aspnet.config 檔中設定 ASP.NET 全處理序行為，當 ASP.NET 裝載於 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="3edc3-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="3edc3-127">此範例假設 IIS 正在執行中整合式驗證模式和應用程式使用.NET Framework 3.5 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3edc3-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="3edc3-128">在.NET Framework 3.5 SP1 之前的.NET framework 的版本中，不會發生此行為。</span><span class="sxs-lookup"><span data-stu-id="3edc3-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="3edc3-129">在範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="3edc3-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="3edc3-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="3edc3-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3edc3-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="3edc3-131">Namespace</span></span>||  
|<span data-ttu-id="3edc3-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="3edc3-132">Schema Name</span></span>||  
|<span data-ttu-id="3edc3-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="3edc3-133">Validation File</span></span>||  
|<span data-ttu-id="3edc3-134">可以是空白</span><span class="sxs-lookup"><span data-stu-id="3edc3-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="3edc3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3edc3-135">See also</span></span>

- [<span data-ttu-id="3edc3-136">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="3edc3-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
