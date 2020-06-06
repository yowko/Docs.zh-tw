---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850215"
---
# \<baseAddresses>
<span data-ttu-id="e55c8-101">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="e55c8-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="e55c8-102">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="e55c8-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="e55c8-103">語法</span><span class="sxs-lookup"><span data-stu-id="e55c8-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="e55c8-104">類型</span><span class="sxs-lookup"><span data-stu-id="e55c8-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e55c8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e55c8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e55c8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e55c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e55c8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e55c8-107">Attributes</span></span>  
 <span data-ttu-id="e55c8-108">無。</span><span class="sxs-lookup"><span data-stu-id="e55c8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e55c8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e55c8-109">Child Elements</span></span>  
  
|<span data-ttu-id="e55c8-110">元素</span><span class="sxs-lookup"><span data-stu-id="e55c8-110">Element</span></span>|<span data-ttu-id="e55c8-111">描述</span><span class="sxs-lookup"><span data-stu-id="e55c8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="e55c8-112">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="e55c8-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e55c8-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e55c8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e55c8-114">元素</span><span class="sxs-lookup"><span data-stu-id="e55c8-114">Element</span></span>|<span data-ttu-id="e55c8-115">描述</span><span class="sxs-lookup"><span data-stu-id="e55c8-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="e55c8-116">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="e55c8-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e55c8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e55c8-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="e55c8-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="e55c8-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
