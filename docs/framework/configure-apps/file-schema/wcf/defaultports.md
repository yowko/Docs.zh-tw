---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925893"
---
# <a name="defaultports"></a><span data-ttu-id="33053-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="33053-101">\<defaultPorts></span></span>
<span data-ttu-id="33053-102">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="33053-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="33053-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="33053-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="33053-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="33053-104">\<behaviors></span></span>  
<span data-ttu-id="33053-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="33053-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="33053-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="33053-106">\<behavior></span></span>  
<span data-ttu-id="33053-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="33053-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="33053-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="33053-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33053-109">語法</span><span class="sxs-lookup"><span data-stu-id="33053-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33053-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="33053-110">Attributes and Elements</span></span>  
 <span data-ttu-id="33053-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="33053-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33053-112">屬性</span><span class="sxs-lookup"><span data-stu-id="33053-112">Attributes</span></span>  
 <span data-ttu-id="33053-113">無。</span><span class="sxs-lookup"><span data-stu-id="33053-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="33053-114">子元素</span><span class="sxs-lookup"><span data-stu-id="33053-114">Child Elements</span></span>  
  
|<span data-ttu-id="33053-115">項目</span><span class="sxs-lookup"><span data-stu-id="33053-115">Element</span></span>|<span data-ttu-id="33053-116">說明</span><span class="sxs-lookup"><span data-stu-id="33053-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33053-117">\<新增 defaultPorts > \<的 ></span><span class="sxs-lookup"><span data-stu-id="33053-117">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="33053-118">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="33053-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33053-119">父項目</span><span class="sxs-lookup"><span data-stu-id="33053-119">Parent Elements</span></span>  
  
|<span data-ttu-id="33053-120">項目</span><span class="sxs-lookup"><span data-stu-id="33053-120">Element</span></span>|<span data-ttu-id="33053-121">描述</span><span class="sxs-lookup"><span data-stu-id="33053-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33053-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="33053-122">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="33053-123">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="33053-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33053-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33053-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
