---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 6c03057fca23b037702c702b9a574045ebb302b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656619"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="7b79d-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="7b79d-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="7b79d-103">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="7b79d-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="7b79d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b79d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b79d-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="7b79d-105">\<behaviors></span></span>  
<span data-ttu-id="7b79d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7b79d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b79d-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7b79d-107">\<behavior></span></span>  
<span data-ttu-id="7b79d-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="7b79d-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b79d-109">語法</span><span class="sxs-lookup"><span data-stu-id="7b79d-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b79d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b79d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b79d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b79d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b79d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7b79d-112">Attributes</span></span>  
 <span data-ttu-id="7b79d-113">無。</span><span class="sxs-lookup"><span data-stu-id="7b79d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b79d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7b79d-114">Child Elements</span></span>  
  
|<span data-ttu-id="7b79d-115">項目</span><span class="sxs-lookup"><span data-stu-id="7b79d-115">Element</span></span>|<span data-ttu-id="7b79d-116">描述</span><span class="sxs-lookup"><span data-stu-id="7b79d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b79d-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="7b79d-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="7b79d-118">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="7b79d-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b79d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7b79d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b79d-120">項目</span><span class="sxs-lookup"><span data-stu-id="7b79d-120">Element</span></span>|<span data-ttu-id="7b79d-121">描述</span><span class="sxs-lookup"><span data-stu-id="7b79d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b79d-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7b79d-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7b79d-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="7b79d-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b79d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b79d-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
