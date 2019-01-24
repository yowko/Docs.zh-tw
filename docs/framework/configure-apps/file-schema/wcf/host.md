---
title: '&lt;host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 1fb35058d407d0fbae78092bb4ccd45b0aaa40e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702024"
---
# <a name="lthostgt"></a><span data-ttu-id="ce0d9-102">&lt;host&gt;</span><span class="sxs-lookup"><span data-stu-id="ce0d9-102">&lt;host&gt;</span></span>
<span data-ttu-id="ce0d9-103">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="ce0d9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ce0d9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce0d9-105">\<services></span><span class="sxs-lookup"><span data-stu-id="ce0d9-105">\<services></span></span>  
<span data-ttu-id="ce0d9-106">\<service></span><span class="sxs-lookup"><span data-stu-id="ce0d9-106">\<service></span></span>  
<span data-ttu-id="ce0d9-107">\<host></span><span class="sxs-lookup"><span data-stu-id="ce0d9-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce0d9-108">語法</span><span class="sxs-lookup"><span data-stu-id="ce0d9-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="ce0d9-109">類型</span><span class="sxs-lookup"><span data-stu-id="ce0d9-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce0d9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce0d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ce0d9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce0d9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ce0d9-112">Attributes</span></span>  
 <span data-ttu-id="ce0d9-113">無。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ce0d9-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ce0d9-114">Child Elements</span></span>  
  
|<span data-ttu-id="ce0d9-115">項目</span><span class="sxs-lookup"><span data-stu-id="ce0d9-115">Element</span></span>|<span data-ttu-id="ce0d9-116">描述</span><span class="sxs-lookup"><span data-stu-id="ce0d9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0d9-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="ce0d9-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="ce0d9-118">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="ce0d9-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="ce0d9-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="ce0d9-120">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce0d9-121">父項目</span><span class="sxs-lookup"><span data-stu-id="ce0d9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce0d9-122">項目</span><span class="sxs-lookup"><span data-stu-id="ce0d9-122">Element</span></span>|<span data-ttu-id="ce0d9-123">描述</span><span class="sxs-lookup"><span data-stu-id="ce0d9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0d9-124">\<service></span><span class="sxs-lookup"><span data-stu-id="ce0d9-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="ce0d9-125">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="ce0d9-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce0d9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce0d9-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ce0d9-127">裝載</span><span class="sxs-lookup"><span data-stu-id="ce0d9-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
