---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="111f9-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="111f9-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="111f9-103">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="111f9-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="111f9-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="111f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="111f9-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="111f9-105">\<behaviors></span></span>  
<span data-ttu-id="111f9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="111f9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="111f9-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="111f9-107">\<behavior></span></span>  
<span data-ttu-id="111f9-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="111f9-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="111f9-109">語法</span><span class="sxs-lookup"><span data-stu-id="111f9-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="111f9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="111f9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="111f9-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="111f9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="111f9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="111f9-112">Attributes</span></span>  
 <span data-ttu-id="111f9-113">無。</span><span class="sxs-lookup"><span data-stu-id="111f9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="111f9-114">子項目</span><span class="sxs-lookup"><span data-stu-id="111f9-114">Child Elements</span></span>  
  
|<span data-ttu-id="111f9-115">項目</span><span class="sxs-lookup"><span data-stu-id="111f9-115">Element</span></span>|<span data-ttu-id="111f9-116">說明</span><span class="sxs-lookup"><span data-stu-id="111f9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="111f9-117">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="111f9-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="111f9-118">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="111f9-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="111f9-119">父項目</span><span class="sxs-lookup"><span data-stu-id="111f9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="111f9-120">項目</span><span class="sxs-lookup"><span data-stu-id="111f9-120">Element</span></span>|<span data-ttu-id="111f9-121">說明</span><span class="sxs-lookup"><span data-stu-id="111f9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="111f9-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="111f9-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="111f9-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="111f9-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="111f9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="111f9-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
