---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398064"
---
# <a name="defaultports"></a><span data-ttu-id="7f534-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="7f534-101">\<defaultPorts></span></span>
<span data-ttu-id="7f534-102">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="7f534-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="7f534-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f534-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7f534-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7f534-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="7f534-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="7f534-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="7f534-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="7f534-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultPorts >**</span><span class="sxs-lookup"><span data-stu-id="7f534-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f534-110">語法</span><span class="sxs-lookup"><span data-stu-id="7f534-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f534-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f534-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7f534-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7f534-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f534-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7f534-113">Attributes</span></span>  
 <span data-ttu-id="7f534-114">無。</span><span class="sxs-lookup"><span data-stu-id="7f534-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f534-115">子元素</span><span class="sxs-lookup"><span data-stu-id="7f534-115">Child Elements</span></span>  
  
|<span data-ttu-id="7f534-116">項目</span><span class="sxs-lookup"><span data-stu-id="7f534-116">Element</span></span>|<span data-ttu-id="7f534-117">說明</span><span class="sxs-lookup"><span data-stu-id="7f534-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f534-118">\<新增 defaultPorts > \<的 ></span><span class="sxs-lookup"><span data-stu-id="7f534-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="7f534-119">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="7f534-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f534-120">父項目</span><span class="sxs-lookup"><span data-stu-id="7f534-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7f534-121">項目</span><span class="sxs-lookup"><span data-stu-id="7f534-121">Element</span></span>|<span data-ttu-id="7f534-122">描述</span><span class="sxs-lookup"><span data-stu-id="7f534-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f534-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="7f534-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="7f534-124">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="7f534-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f534-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f534-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
