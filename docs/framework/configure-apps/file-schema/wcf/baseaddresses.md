---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850215"
---
# <a name="baseaddresses"></a><span data-ttu-id="c1145-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="c1145-101">\<baseAddresses></span></span>
<span data-ttu-id="c1145-102">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="c1145-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="c1145-103">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="c1145-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="c1145-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1145-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1145-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c1145-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c1145-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="c1145-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="c1145-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="c1145-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="c1145-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<主機 >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="c1145-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="c1145-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddresses >**</span><span class="sxs-lookup"><span data-stu-id="c1145-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1145-110">語法</span><span class="sxs-lookup"><span data-stu-id="c1145-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="c1145-111">類型</span><span class="sxs-lookup"><span data-stu-id="c1145-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1145-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1145-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c1145-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c1145-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1145-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c1145-114">Attributes</span></span>  
 <span data-ttu-id="c1145-115">無。</span><span class="sxs-lookup"><span data-stu-id="c1145-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1145-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c1145-116">Child Elements</span></span>  
  
|<span data-ttu-id="c1145-117">項目</span><span class="sxs-lookup"><span data-stu-id="c1145-117">Element</span></span>|<span data-ttu-id="c1145-118">描述</span><span class="sxs-lookup"><span data-stu-id="c1145-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1145-119">\<add></span><span class="sxs-lookup"><span data-stu-id="c1145-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="c1145-120">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="c1145-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1145-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c1145-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c1145-122">項目</span><span class="sxs-lookup"><span data-stu-id="c1145-122">Element</span></span>|<span data-ttu-id="c1145-123">描述</span><span class="sxs-lookup"><span data-stu-id="c1145-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1145-124">\<host></span><span class="sxs-lookup"><span data-stu-id="c1145-124">\<host></span></span>](host.md)|<span data-ttu-id="c1145-125">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="c1145-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1145-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1145-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c1145-127">裝載</span><span class="sxs-lookup"><span data-stu-id="c1145-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
