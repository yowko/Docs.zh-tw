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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152837"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="dc8d0-102">\<系統.web>元素（Web 設置）</span><span class="sxs-lookup"><span data-stu-id="dc8d0-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="dc8d0-103">包含有關託管層如何管理進程範圍行為ASP.NET的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="dc8d0-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="dc8d0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="dc8d0-105">&nbsp;&nbsp;**\<系統.web>**</span><span class="sxs-lookup"><span data-stu-id="dc8d0-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8d0-106">語法</span><span class="sxs-lookup"><span data-stu-id="dc8d0-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc8d0-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc8d0-107">Attributes and Elements</span></span>  

<span data-ttu-id="dc8d0-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc8d0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dc8d0-109">Attributes</span></span>  

<span data-ttu-id="dc8d0-110">無。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc8d0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc8d0-111">Child Elements</span></span>  
  
|<span data-ttu-id="dc8d0-112">元素</span><span class="sxs-lookup"><span data-stu-id="dc8d0-112">Element</span></span>|<span data-ttu-id="dc8d0-113">描述</span><span class="sxs-lookup"><span data-stu-id="dc8d0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc8d0-114">\<應用程式池></span><span class="sxs-lookup"><span data-stu-id="dc8d0-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="dc8d0-115">在 aspnet.config 檔中指定 IIS 應用程式池的配置設置。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc8d0-116">父項目</span><span class="sxs-lookup"><span data-stu-id="dc8d0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dc8d0-117">元素</span><span class="sxs-lookup"><span data-stu-id="dc8d0-117">Element</span></span>|<span data-ttu-id="dc8d0-118">描述</span><span class="sxs-lookup"><span data-stu-id="dc8d0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc8d0-119">\<配置></span><span class="sxs-lookup"><span data-stu-id="dc8d0-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="dc8d0-120">指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc8d0-121">備註</span><span class="sxs-lookup"><span data-stu-id="dc8d0-121">Remarks</span></span>  

<span data-ttu-id="dc8d0-122">該`system.web`元素及其子`applicationPool`元素從 .NET 框架 3.5 SP1 開始添加到 .NET 框架中。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="dc8d0-123">在整合模式下運行 IIS 7.0 或更高版本時，此元素組合允許您配置ASP.NET如何管理執行緒以及ASP.NET託管在 IIS 應用程式池中時如何排隊請求。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="dc8d0-124">如果在經典或 ISAPI 模式下運行 IIS 7.0 或更高版本，則忽略這些設置。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8d0-125">範例</span><span class="sxs-lookup"><span data-stu-id="dc8d0-125">Example</span></span>  

<span data-ttu-id="dc8d0-126">下面的示例演示如何在 iIS 應用程式池中託管ASP.NET時，如何在 aspnet.config 檔中配置ASP.NET進程範圍的行為。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="dc8d0-127">該示例假定 IIS 在整合模式下運行，並且應用程式正在使用 .NET 框架 3.5 SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="dc8d0-128">此行為不會在 .NET 框架 3.5 SP1 之前的版本中發生。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="dc8d0-129">示例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="dc8d0-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="dc8d0-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="dc8d0-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc8d0-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="dc8d0-131">Namespace</span></span>||  
|<span data-ttu-id="dc8d0-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="dc8d0-132">Schema Name</span></span>||  
|<span data-ttu-id="dc8d0-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="dc8d0-133">Validation File</span></span>||  
|<span data-ttu-id="dc8d0-134">可以為空</span><span class="sxs-lookup"><span data-stu-id="dc8d0-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="dc8d0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc8d0-135">See also</span></span>

- [<span data-ttu-id="dc8d0-136">\<應用程式池>元素（Web 設置）</span><span class="sxs-lookup"><span data-stu-id="dc8d0-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
