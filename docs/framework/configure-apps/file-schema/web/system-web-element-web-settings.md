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
ms.openlocfilehash: c8b01ec217fc1b6b91ccf36c8667922b57f26852
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185583"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="86a3b-102">\<system.web> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="86a3b-102">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="86a3b-103">包含 ASP.NET 裝載層如何管理整個進程行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="86a3b-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="86a3b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="86a3b-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86a3b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86a3b-105">Attributes and Elements</span></span>  

<span data-ttu-id="86a3b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86a3b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86a3b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="86a3b-107">Attributes</span></span>  

<span data-ttu-id="86a3b-108">無。</span><span class="sxs-lookup"><span data-stu-id="86a3b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="86a3b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="86a3b-109">Child Elements</span></span>  
  
|<span data-ttu-id="86a3b-110">項目</span><span class="sxs-lookup"><span data-stu-id="86a3b-110">Element</span></span>|<span data-ttu-id="86a3b-111">描述</span><span class="sxs-lookup"><span data-stu-id="86a3b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="86a3b-112">在 aspnet.config 檔案中指定 IIS 應用程式集區的設定。</span><span class="sxs-lookup"><span data-stu-id="86a3b-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86a3b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="86a3b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="86a3b-114">項目</span><span class="sxs-lookup"><span data-stu-id="86a3b-114">Element</span></span>|<span data-ttu-id="86a3b-115">描述</span><span class="sxs-lookup"><span data-stu-id="86a3b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="86a3b-116">指定 common language runtime 和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="86a3b-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86a3b-117">備註</span><span class="sxs-lookup"><span data-stu-id="86a3b-117">Remarks</span></span>  

<span data-ttu-id="86a3b-118">從 `system.web` `applicationPool` .NET FRAMEWORK 3.5 SP1 以來，元素和其子項目已新增至 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="86a3b-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="86a3b-119">當您在整合模式中執行 IIS 7.0 或更新版本時，此元素組合可讓您設定 ASP.NET 管理執行緒的方式，以及在 ASP.NET 裝載于 IIS 應用程式集區時，它如何將要求排入佇列。</span><span class="sxs-lookup"><span data-stu-id="86a3b-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="86a3b-120">如果您在傳統或 ISAPI 模式中執行 IIS 7.0 或更新版本，則會忽略這些設定。</span><span class="sxs-lookup"><span data-stu-id="86a3b-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a3b-121">範例</span><span class="sxs-lookup"><span data-stu-id="86a3b-121">Example</span></span>  

<span data-ttu-id="86a3b-122">下列範例示範如何在 ASP.NET 裝載于 IIS 應用程式集區時，在 aspnet.config 檔案中設定 ASP.NET 全進程的行為。</span><span class="sxs-lookup"><span data-stu-id="86a3b-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="86a3b-123">此範例假設 IIS 是以整合模式執行，且應用程式使用 .NET Framework 3.5 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="86a3b-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="86a3b-124">在 .NET Framework 3.5 SP1 之前的 .NET Framework 版本中，不會發生此行為。</span><span class="sxs-lookup"><span data-stu-id="86a3b-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="86a3b-125">範例中的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="86a3b-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="86a3b-126">項目資訊</span><span class="sxs-lookup"><span data-stu-id="86a3b-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86a3b-127">命名空間</span><span class="sxs-lookup"><span data-stu-id="86a3b-127">Namespace</span></span>||  
|<span data-ttu-id="86a3b-128">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="86a3b-128">Schema Name</span></span>||  
|<span data-ttu-id="86a3b-129">驗證檔</span><span class="sxs-lookup"><span data-stu-id="86a3b-129">Validation File</span></span>||  
|<span data-ttu-id="86a3b-130">可以是空的</span><span class="sxs-lookup"><span data-stu-id="86a3b-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="86a3b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86a3b-131">See also</span></span>

- [<span data-ttu-id="86a3b-132">\<applicationPool> (Web 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="86a3b-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
