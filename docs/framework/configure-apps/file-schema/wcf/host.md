---
title: '&lt;主應用程式&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: afa9d65223ab3a7730a55bc41ed98458707b32db
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145220"
---
# <a name="lthostgt"></a><span data-ttu-id="436fb-102">&lt;主應用程式&gt;</span><span class="sxs-lookup"><span data-stu-id="436fb-102">&lt;host&gt;</span></span>
<span data-ttu-id="436fb-103">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="436fb-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="436fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="436fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="436fb-105">\<services></span><span class="sxs-lookup"><span data-stu-id="436fb-105">\<services></span></span>  
<span data-ttu-id="436fb-106">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="436fb-106">\<service></span></span>  
<span data-ttu-id="436fb-107">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="436fb-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="436fb-108">語法</span><span class="sxs-lookup"><span data-stu-id="436fb-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="436fb-109">類型</span><span class="sxs-lookup"><span data-stu-id="436fb-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="436fb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="436fb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="436fb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="436fb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="436fb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="436fb-112">Attributes</span></span>  
 <span data-ttu-id="436fb-113">無。</span><span class="sxs-lookup"><span data-stu-id="436fb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="436fb-114">子元素</span><span class="sxs-lookup"><span data-stu-id="436fb-114">Child Elements</span></span>  
  
|<span data-ttu-id="436fb-115">項目</span><span class="sxs-lookup"><span data-stu-id="436fb-115">Element</span></span>|<span data-ttu-id="436fb-116">描述</span><span class="sxs-lookup"><span data-stu-id="436fb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="436fb-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="436fb-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="436fb-118">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="436fb-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="436fb-119">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="436fb-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="436fb-120">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="436fb-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="436fb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="436fb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="436fb-122">項目</span><span class="sxs-lookup"><span data-stu-id="436fb-122">Element</span></span>|<span data-ttu-id="436fb-123">描述</span><span class="sxs-lookup"><span data-stu-id="436fb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="436fb-124">\<service></span><span class="sxs-lookup"><span data-stu-id="436fb-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="436fb-125">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="436fb-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="436fb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="436fb-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="436fb-127">裝載</span><span class="sxs-lookup"><span data-stu-id="436fb-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
