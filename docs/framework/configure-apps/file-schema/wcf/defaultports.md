---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130620"
---
# <a name="defaultports"></a><span data-ttu-id="55e80-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="55e80-101">\<defaultPorts></span></span>
<span data-ttu-id="55e80-102">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="55e80-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="55e80-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="55e80-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="55e80-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="55e80-104">\<behaviors></span></span>  
<span data-ttu-id="55e80-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="55e80-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="55e80-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="55e80-106">\<behavior></span></span>  
<span data-ttu-id="55e80-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="55e80-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="55e80-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="55e80-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e80-109">語法</span><span class="sxs-lookup"><span data-stu-id="55e80-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55e80-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="55e80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55e80-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="55e80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55e80-112">屬性</span><span class="sxs-lookup"><span data-stu-id="55e80-112">Attributes</span></span>  
 <span data-ttu-id="55e80-113">無。</span><span class="sxs-lookup"><span data-stu-id="55e80-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55e80-114">子元素</span><span class="sxs-lookup"><span data-stu-id="55e80-114">Child Elements</span></span>  
  
|<span data-ttu-id="55e80-115">項目</span><span class="sxs-lookup"><span data-stu-id="55e80-115">Element</span></span>|<span data-ttu-id="55e80-116">描述</span><span class="sxs-lookup"><span data-stu-id="55e80-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e80-117">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="55e80-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="55e80-118">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="55e80-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55e80-119">父項目</span><span class="sxs-lookup"><span data-stu-id="55e80-119">Parent Elements</span></span>  
  
|<span data-ttu-id="55e80-120">項目</span><span class="sxs-lookup"><span data-stu-id="55e80-120">Element</span></span>|<span data-ttu-id="55e80-121">描述</span><span class="sxs-lookup"><span data-stu-id="55e80-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e80-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="55e80-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="55e80-123">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="55e80-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55e80-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55e80-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
