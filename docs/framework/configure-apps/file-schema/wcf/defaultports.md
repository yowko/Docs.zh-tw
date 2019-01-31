---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 595970a56e05c4fc1c9b2c0eb669ec3b3a120fe1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262373"
---
# <a name="defaultports"></a><span data-ttu-id="5198e-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5198e-101">\<defaultPorts></span></span>
<span data-ttu-id="5198e-102">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="5198e-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="5198e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5198e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5198e-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5198e-104">\<behaviors></span></span>  
<span data-ttu-id="5198e-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5198e-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5198e-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5198e-106">\<behavior></span></span>  
<span data-ttu-id="5198e-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5198e-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="5198e-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5198e-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5198e-109">語法</span><span class="sxs-lookup"><span data-stu-id="5198e-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5198e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5198e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5198e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5198e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5198e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5198e-112">Attributes</span></span>  
 <span data-ttu-id="5198e-113">無。</span><span class="sxs-lookup"><span data-stu-id="5198e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5198e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="5198e-114">Child Elements</span></span>  
  
|<span data-ttu-id="5198e-115">項目</span><span class="sxs-lookup"><span data-stu-id="5198e-115">Element</span></span>|<span data-ttu-id="5198e-116">描述</span><span class="sxs-lookup"><span data-stu-id="5198e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5198e-117">\<add> of \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5198e-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="5198e-118">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="5198e-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5198e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="5198e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5198e-120">項目</span><span class="sxs-lookup"><span data-stu-id="5198e-120">Element</span></span>|<span data-ttu-id="5198e-121">描述</span><span class="sxs-lookup"><span data-stu-id="5198e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5198e-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5198e-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="5198e-123">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="5198e-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5198e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5198e-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
