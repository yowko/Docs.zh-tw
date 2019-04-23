---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121182"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="94a87-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="94a87-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="94a87-102">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="94a87-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="94a87-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94a87-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="94a87-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="94a87-104">\<behaviors></span></span>  
<span data-ttu-id="94a87-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="94a87-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="94a87-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="94a87-106">\<behavior></span></span>  
<span data-ttu-id="94a87-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="94a87-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a87-108">語法</span><span class="sxs-lookup"><span data-stu-id="94a87-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94a87-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94a87-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94a87-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="94a87-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94a87-111">屬性</span><span class="sxs-lookup"><span data-stu-id="94a87-111">Attributes</span></span>  
 <span data-ttu-id="94a87-112">無。</span><span class="sxs-lookup"><span data-stu-id="94a87-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94a87-113">子元素</span><span class="sxs-lookup"><span data-stu-id="94a87-113">Child Elements</span></span>  
  
|<span data-ttu-id="94a87-114">項目</span><span class="sxs-lookup"><span data-stu-id="94a87-114">Element</span></span>|<span data-ttu-id="94a87-115">描述</span><span class="sxs-lookup"><span data-stu-id="94a87-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94a87-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="94a87-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="94a87-117">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="94a87-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94a87-118">父項目</span><span class="sxs-lookup"><span data-stu-id="94a87-118">Parent Elements</span></span>  
  
|<span data-ttu-id="94a87-119">項目</span><span class="sxs-lookup"><span data-stu-id="94a87-119">Element</span></span>|<span data-ttu-id="94a87-120">描述</span><span class="sxs-lookup"><span data-stu-id="94a87-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94a87-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="94a87-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="94a87-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="94a87-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94a87-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a87-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
