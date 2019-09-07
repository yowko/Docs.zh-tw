---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399195"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="01cd6-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="01cd6-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="01cd6-102">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="01cd6-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="01cd6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="01cd6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="01cd6-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="01cd6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="01cd6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="01cd6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="01cd6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="01cd6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="01cd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="01cd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="01cd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useRequestHeadersForMetadataAddress >**</span><span class="sxs-lookup"><span data-stu-id="01cd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01cd6-109">語法</span><span class="sxs-lookup"><span data-stu-id="01cd6-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01cd6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01cd6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01cd6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="01cd6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01cd6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="01cd6-112">Attributes</span></span>  
 <span data-ttu-id="01cd6-113">無。</span><span class="sxs-lookup"><span data-stu-id="01cd6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01cd6-114">子元素</span><span class="sxs-lookup"><span data-stu-id="01cd6-114">Child Elements</span></span>  
  
|<span data-ttu-id="01cd6-115">項目</span><span class="sxs-lookup"><span data-stu-id="01cd6-115">Element</span></span>|<span data-ttu-id="01cd6-116">描述</span><span class="sxs-lookup"><span data-stu-id="01cd6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01cd6-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="01cd6-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="01cd6-118">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="01cd6-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01cd6-119">父項目</span><span class="sxs-lookup"><span data-stu-id="01cd6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="01cd6-120">項目</span><span class="sxs-lookup"><span data-stu-id="01cd6-120">Element</span></span>|<span data-ttu-id="01cd6-121">描述</span><span class="sxs-lookup"><span data-stu-id="01cd6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01cd6-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="01cd6-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="01cd6-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="01cd6-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01cd6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01cd6-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
