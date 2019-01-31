---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269025"
---
# <a name="host"></a><span data-ttu-id="cdab2-101">\<host></span><span class="sxs-lookup"><span data-stu-id="cdab2-101">\<host></span></span>
<span data-ttu-id="cdab2-102">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="cdab2-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="cdab2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cdab2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="cdab2-104">\<services></span><span class="sxs-lookup"><span data-stu-id="cdab2-104">\<services></span></span>  
<span data-ttu-id="cdab2-105">\<service></span><span class="sxs-lookup"><span data-stu-id="cdab2-105">\<service></span></span>  
<span data-ttu-id="cdab2-106">\<host></span><span class="sxs-lookup"><span data-stu-id="cdab2-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdab2-107">語法</span><span class="sxs-lookup"><span data-stu-id="cdab2-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="cdab2-108">類型</span><span class="sxs-lookup"><span data-stu-id="cdab2-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdab2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdab2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cdab2-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cdab2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdab2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cdab2-111">Attributes</span></span>  
 <span data-ttu-id="cdab2-112">無。</span><span class="sxs-lookup"><span data-stu-id="cdab2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdab2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-113">Child Elements</span></span>  
  
|<span data-ttu-id="cdab2-114">項目</span><span class="sxs-lookup"><span data-stu-id="cdab2-114">Element</span></span>|<span data-ttu-id="cdab2-115">描述</span><span class="sxs-lookup"><span data-stu-id="cdab2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdab2-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="cdab2-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="cdab2-117">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="cdab2-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="cdab2-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="cdab2-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="cdab2-119">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="cdab2-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdab2-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cdab2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cdab2-121">項目</span><span class="sxs-lookup"><span data-stu-id="cdab2-121">Element</span></span>|<span data-ttu-id="cdab2-122">描述</span><span class="sxs-lookup"><span data-stu-id="cdab2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdab2-123">\<service></span><span class="sxs-lookup"><span data-stu-id="cdab2-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="cdab2-124">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="cdab2-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdab2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdab2-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="cdab2-126">裝載</span><span class="sxs-lookup"><span data-stu-id="cdab2-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
