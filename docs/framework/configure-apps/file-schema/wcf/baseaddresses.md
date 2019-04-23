---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 7d0afd638e9a311b69ff47b6789d5fde093945ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212098"
---
# <a name="baseaddresses"></a><span data-ttu-id="90db4-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="90db4-101">\<baseAddresses></span></span>
<span data-ttu-id="90db4-102">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="90db4-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="90db4-103">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="90db4-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="90db4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90db4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90db4-105">\<client></span><span class="sxs-lookup"><span data-stu-id="90db4-105">\<client></span></span>  
<span data-ttu-id="90db4-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="90db4-106">\<endpoint></span></span>  
<span data-ttu-id="90db4-107">\<host></span><span class="sxs-lookup"><span data-stu-id="90db4-107">\<host></span></span>  
<span data-ttu-id="90db4-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="90db4-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90db4-109">語法</span><span class="sxs-lookup"><span data-stu-id="90db4-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="90db4-110">類型</span><span class="sxs-lookup"><span data-stu-id="90db4-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90db4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90db4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="90db4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90db4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90db4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="90db4-113">Attributes</span></span>  
 <span data-ttu-id="90db4-114">無。</span><span class="sxs-lookup"><span data-stu-id="90db4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90db4-115">子元素</span><span class="sxs-lookup"><span data-stu-id="90db4-115">Child Elements</span></span>  
  
|<span data-ttu-id="90db4-116">項目</span><span class="sxs-lookup"><span data-stu-id="90db4-116">Element</span></span>|<span data-ttu-id="90db4-117">描述</span><span class="sxs-lookup"><span data-stu-id="90db4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90db4-118">\<add></span><span class="sxs-lookup"><span data-stu-id="90db4-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="90db4-119">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="90db4-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90db4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="90db4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="90db4-121">項目</span><span class="sxs-lookup"><span data-stu-id="90db4-121">Element</span></span>|<span data-ttu-id="90db4-122">描述</span><span class="sxs-lookup"><span data-stu-id="90db4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90db4-123">\<host></span><span class="sxs-lookup"><span data-stu-id="90db4-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="90db4-124">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="90db4-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90db4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90db4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="90db4-126">裝載</span><span class="sxs-lookup"><span data-stu-id="90db4-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
