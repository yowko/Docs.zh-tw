---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918713"
---
# <a name="host"></a><span data-ttu-id="d9796-101">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="d9796-101">\<host></span></span>
<span data-ttu-id="d9796-102">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="d9796-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="d9796-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9796-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9796-104">\<services></span><span class="sxs-lookup"><span data-stu-id="d9796-104">\<services></span></span>  
<span data-ttu-id="d9796-105">\<service></span><span class="sxs-lookup"><span data-stu-id="d9796-105">\<service></span></span>  
<span data-ttu-id="d9796-106">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="d9796-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9796-107">語法</span><span class="sxs-lookup"><span data-stu-id="d9796-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="d9796-108">類型</span><span class="sxs-lookup"><span data-stu-id="d9796-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9796-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9796-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d9796-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d9796-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9796-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d9796-111">Attributes</span></span>  
 <span data-ttu-id="d9796-112">無。</span><span class="sxs-lookup"><span data-stu-id="d9796-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9796-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d9796-113">Child Elements</span></span>  
  
|<span data-ttu-id="d9796-114">項目</span><span class="sxs-lookup"><span data-stu-id="d9796-114">Element</span></span>|<span data-ttu-id="d9796-115">說明</span><span class="sxs-lookup"><span data-stu-id="d9796-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9796-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="d9796-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="d9796-117">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="d9796-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="d9796-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="d9796-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="d9796-119">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d9796-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9796-120">父項目</span><span class="sxs-lookup"><span data-stu-id="d9796-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d9796-121">項目</span><span class="sxs-lookup"><span data-stu-id="d9796-121">Element</span></span>|<span data-ttu-id="d9796-122">說明</span><span class="sxs-lookup"><span data-stu-id="d9796-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9796-123">\<service></span><span class="sxs-lookup"><span data-stu-id="d9796-123">\<service></span></span>](service.md)|<span data-ttu-id="d9796-124">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="d9796-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9796-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9796-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="d9796-126">裝載</span><span class="sxs-lookup"><span data-stu-id="d9796-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
