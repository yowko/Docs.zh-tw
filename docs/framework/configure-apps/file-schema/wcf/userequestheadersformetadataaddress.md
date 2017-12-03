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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e7f69da871376f83422fb330f8babd56bb1fdcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="56270-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="56270-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="56270-103">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="56270-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="56270-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="56270-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="56270-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="56270-105">\<behaviors></span></span>  
<span data-ttu-id="56270-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="56270-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="56270-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="56270-107">\<behavior></span></span>  
<span data-ttu-id="56270-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="56270-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56270-109">語法</span><span class="sxs-lookup"><span data-stu-id="56270-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56270-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56270-110">Attributes and Elements</span></span>  
 <span data-ttu-id="56270-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56270-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56270-112">屬性</span><span class="sxs-lookup"><span data-stu-id="56270-112">Attributes</span></span>  
 <span data-ttu-id="56270-113">無。</span><span class="sxs-lookup"><span data-stu-id="56270-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56270-114">子項目</span><span class="sxs-lookup"><span data-stu-id="56270-114">Child Elements</span></span>  
  
|<span data-ttu-id="56270-115">項目</span><span class="sxs-lookup"><span data-stu-id="56270-115">Element</span></span>|<span data-ttu-id="56270-116">說明</span><span class="sxs-lookup"><span data-stu-id="56270-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56270-117">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="56270-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="56270-118">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="56270-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56270-119">父項目</span><span class="sxs-lookup"><span data-stu-id="56270-119">Parent Elements</span></span>  
  
|<span data-ttu-id="56270-120">項目</span><span class="sxs-lookup"><span data-stu-id="56270-120">Element</span></span>|<span data-ttu-id="56270-121">說明</span><span class="sxs-lookup"><span data-stu-id="56270-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56270-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="56270-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="56270-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="56270-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56270-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56270-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
