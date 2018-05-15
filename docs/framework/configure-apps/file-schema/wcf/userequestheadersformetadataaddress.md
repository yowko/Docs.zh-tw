---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="90d52-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="90d52-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="90d52-103">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="90d52-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="90d52-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90d52-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90d52-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="90d52-105">\<behaviors></span></span>  
<span data-ttu-id="90d52-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="90d52-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="90d52-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="90d52-107">\<behavior></span></span>  
<span data-ttu-id="90d52-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="90d52-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d52-109">語法</span><span class="sxs-lookup"><span data-stu-id="90d52-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90d52-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90d52-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90d52-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90d52-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90d52-112">屬性</span><span class="sxs-lookup"><span data-stu-id="90d52-112">Attributes</span></span>  
 <span data-ttu-id="90d52-113">無。</span><span class="sxs-lookup"><span data-stu-id="90d52-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90d52-114">子項目</span><span class="sxs-lookup"><span data-stu-id="90d52-114">Child Elements</span></span>  
  
|<span data-ttu-id="90d52-115">項目</span><span class="sxs-lookup"><span data-stu-id="90d52-115">Element</span></span>|<span data-ttu-id="90d52-116">描述</span><span class="sxs-lookup"><span data-stu-id="90d52-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d52-117">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="90d52-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="90d52-118">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="90d52-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90d52-119">父項目</span><span class="sxs-lookup"><span data-stu-id="90d52-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90d52-120">項目</span><span class="sxs-lookup"><span data-stu-id="90d52-120">Element</span></span>|<span data-ttu-id="90d52-121">描述</span><span class="sxs-lookup"><span data-stu-id="90d52-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d52-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="90d52-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="90d52-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="90d52-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90d52-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90d52-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
