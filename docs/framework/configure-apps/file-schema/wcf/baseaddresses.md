---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926416"
---
# <a name="baseaddresses"></a><span data-ttu-id="393c6-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="393c6-101">\<baseAddresses></span></span>
<span data-ttu-id="393c6-102">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="393c6-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="393c6-103">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="393c6-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="393c6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="393c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="393c6-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="393c6-105">\<client></span></span>  
<span data-ttu-id="393c6-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="393c6-106">\<endpoint></span></span>  
<span data-ttu-id="393c6-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="393c6-107">\<host></span></span>  
<span data-ttu-id="393c6-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="393c6-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="393c6-109">語法</span><span class="sxs-lookup"><span data-stu-id="393c6-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="393c6-110">類型</span><span class="sxs-lookup"><span data-stu-id="393c6-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="393c6-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="393c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="393c6-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="393c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="393c6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="393c6-113">Attributes</span></span>  
 <span data-ttu-id="393c6-114">無。</span><span class="sxs-lookup"><span data-stu-id="393c6-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="393c6-115">子元素</span><span class="sxs-lookup"><span data-stu-id="393c6-115">Child Elements</span></span>  
  
|<span data-ttu-id="393c6-116">項目</span><span class="sxs-lookup"><span data-stu-id="393c6-116">Element</span></span>|<span data-ttu-id="393c6-117">描述</span><span class="sxs-lookup"><span data-stu-id="393c6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="393c6-118">\<add></span><span class="sxs-lookup"><span data-stu-id="393c6-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="393c6-119">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="393c6-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="393c6-120">父項目</span><span class="sxs-lookup"><span data-stu-id="393c6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="393c6-121">項目</span><span class="sxs-lookup"><span data-stu-id="393c6-121">Element</span></span>|<span data-ttu-id="393c6-122">描述</span><span class="sxs-lookup"><span data-stu-id="393c6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="393c6-123">\<host></span><span class="sxs-lookup"><span data-stu-id="393c6-123">\<host></span></span>](host.md)|<span data-ttu-id="393c6-124">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="393c6-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="393c6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="393c6-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="393c6-126">裝載</span><span class="sxs-lookup"><span data-stu-id="393c6-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
