---
title: '&lt;a d d&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2f7de066a1b91e9fa22fbe0213e221c6f4bbe617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="e816f-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="e816f-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="e816f-103">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="e816f-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="e816f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e816f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e816f-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e816f-105">\<behaviors></span></span>  
<span data-ttu-id="e816f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e816f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e816f-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e816f-107">\<behavior></span></span>  
<span data-ttu-id="e816f-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="e816f-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="e816f-109">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="e816f-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e816f-110">語法</span><span class="sxs-lookup"><span data-stu-id="e816f-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e816f-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e816f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e816f-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e816f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e816f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e816f-113">Attributes</span></span>  
 <span data-ttu-id="e816f-114">無。</span><span class="sxs-lookup"><span data-stu-id="e816f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e816f-115">子項目</span><span class="sxs-lookup"><span data-stu-id="e816f-115">Child Elements</span></span>  
  
|<span data-ttu-id="e816f-116">項目</span><span class="sxs-lookup"><span data-stu-id="e816f-116">Element</span></span>|<span data-ttu-id="e816f-117">描述</span><span class="sxs-lookup"><span data-stu-id="e816f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e816f-118">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="e816f-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="e816f-119">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="e816f-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e816f-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e816f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e816f-121">項目</span><span class="sxs-lookup"><span data-stu-id="e816f-121">Element</span></span>|<span data-ttu-id="e816f-122">描述</span><span class="sxs-lookup"><span data-stu-id="e816f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e816f-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="e816f-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="e816f-124">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="e816f-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e816f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e816f-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
