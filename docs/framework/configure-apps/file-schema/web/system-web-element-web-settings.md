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
ms.openlocfilehash: 41a638afa93e605221d5ef8172e243b1c61676bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941388"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="2c9c2-102">\<system.web > 元素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="2c9c2-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="2c9c2-103">包含 ASP.NET 裝載層如何管理整個進程行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="2c9c2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c9c2-104">\<configuration></span></span>  
<span data-ttu-id="2c9c2-105">\<system.web > 元素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="2c9c2-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9c2-106">語法</span><span class="sxs-lookup"><span data-stu-id="2c9c2-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c9c2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c9c2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2c9c2-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c9c2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2c9c2-109">Attributes</span></span>  
 <span data-ttu-id="2c9c2-110">無。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c9c2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2c9c2-111">Child Elements</span></span>  
  
|<span data-ttu-id="2c9c2-112">項目</span><span class="sxs-lookup"><span data-stu-id="2c9c2-112">Element</span></span>|<span data-ttu-id="2c9c2-113">描述</span><span class="sxs-lookup"><span data-stu-id="2c9c2-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c9c2-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="2c9c2-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="2c9c2-115">在 aspnet .config 檔案中指定 IIS 應用程式集區的配置設定。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c9c2-116">父項目</span><span class="sxs-lookup"><span data-stu-id="2c9c2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2c9c2-117">項目</span><span class="sxs-lookup"><span data-stu-id="2c9c2-117">Element</span></span>|<span data-ttu-id="2c9c2-118">說明</span><span class="sxs-lookup"><span data-stu-id="2c9c2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c9c2-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c9c2-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="2c9c2-120">指定通用語言執行時間和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c9c2-121">備註</span><span class="sxs-lookup"><span data-stu-id="2c9c2-121">Remarks</span></span>  
 <span data-ttu-id="2c9c2-122">元素及其子`applicationPool`專案已加入至 .NET Framework, 從 .NET Framework 3.5 SP1。 `system.web`</span><span class="sxs-lookup"><span data-stu-id="2c9c2-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="2c9c2-123">當您在整合模式中執行 IIS 7.0 或更新版本時, 此元素組合可讓您設定 ASP.NET 管理執行緒的方式, 以及當 ASP.NET 裝載于 IIS 應用程式集區時, 如何將要求排入佇列。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="2c9c2-124">如果您以傳統或 ISAPI 模式執行 IIS 7.0 或更新版本, 則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c9c2-125">範例</span><span class="sxs-lookup"><span data-stu-id="2c9c2-125">Example</span></span>  
 <span data-ttu-id="2c9c2-126">下列範例顯示當 ASP.NET 裝載于 IIS 應用程式集區時, 如何在 aspnet .config 檔案中設定 ASP.NET 全進程行為。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="2c9c2-127">此範例假設 IIS 是在整合模式中執行, 且應用程式使用 .NET Framework 3.5 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="2c9c2-128">這種行為不會發生在 .NET Framework 3.5 SP1 之前的 .NET Framework 版本中。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="2c9c2-129">範例中的值為預設值。</span><span class="sxs-lookup"><span data-stu-id="2c9c2-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="2c9c2-130">項目資訊</span><span class="sxs-lookup"><span data-stu-id="2c9c2-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c9c2-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="2c9c2-131">Namespace</span></span>||  
|<span data-ttu-id="2c9c2-132">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="2c9c2-132">Schema Name</span></span>||  
|<span data-ttu-id="2c9c2-133">驗證檔</span><span class="sxs-lookup"><span data-stu-id="2c9c2-133">Validation File</span></span>||  
|<span data-ttu-id="2c9c2-134">可以是空的</span><span class="sxs-lookup"><span data-stu-id="2c9c2-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2c9c2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c9c2-135">See also</span></span>

- [<span data-ttu-id="2c9c2-136">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="2c9c2-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
