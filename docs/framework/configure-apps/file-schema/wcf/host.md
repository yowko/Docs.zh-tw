---
title: '&lt;主機&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 9c48fff7473449192887bfd8cc201dd87cb4e7f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lthostgt"></a><span data-ttu-id="69c32-102">&lt;主機&gt;</span><span class="sxs-lookup"><span data-stu-id="69c32-102">&lt;host&gt;</span></span>
<span data-ttu-id="69c32-103">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="69c32-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="69c32-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69c32-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69c32-105">\<services></span><span class="sxs-lookup"><span data-stu-id="69c32-105">\<services></span></span>  
<span data-ttu-id="69c32-106">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="69c32-106">\<service></span></span>  
<span data-ttu-id="69c32-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="69c32-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c32-108">語法</span><span class="sxs-lookup"><span data-stu-id="69c32-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="69c32-109">類型</span><span class="sxs-lookup"><span data-stu-id="69c32-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69c32-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="69c32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="69c32-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="69c32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69c32-112">屬性</span><span class="sxs-lookup"><span data-stu-id="69c32-112">Attributes</span></span>  
 <span data-ttu-id="69c32-113">無。</span><span class="sxs-lookup"><span data-stu-id="69c32-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69c32-114">子項目</span><span class="sxs-lookup"><span data-stu-id="69c32-114">Child Elements</span></span>  
  
|<span data-ttu-id="69c32-115">項目</span><span class="sxs-lookup"><span data-stu-id="69c32-115">Element</span></span>|<span data-ttu-id="69c32-116">描述</span><span class="sxs-lookup"><span data-stu-id="69c32-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69c32-117">\<s ></span><span class="sxs-lookup"><span data-stu-id="69c32-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="69c32-118">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="69c32-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="69c32-119">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="69c32-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="69c32-120">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="69c32-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69c32-121">父項目</span><span class="sxs-lookup"><span data-stu-id="69c32-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69c32-122">項目</span><span class="sxs-lookup"><span data-stu-id="69c32-122">Element</span></span>|<span data-ttu-id="69c32-123">描述</span><span class="sxs-lookup"><span data-stu-id="69c32-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69c32-124">\<service></span><span class="sxs-lookup"><span data-stu-id="69c32-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="69c32-125">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="69c32-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69c32-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69c32-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="69c32-127">裝載</span><span class="sxs-lookup"><span data-stu-id="69c32-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
