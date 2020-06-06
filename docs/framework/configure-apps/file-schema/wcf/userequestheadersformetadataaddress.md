---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399195"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="306db-101">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="306db-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="306db-102">語法</span><span class="sxs-lookup"><span data-stu-id="306db-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="306db-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="306db-103">Attributes and Elements</span></span>  
 <span data-ttu-id="306db-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="306db-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="306db-105">屬性</span><span class="sxs-lookup"><span data-stu-id="306db-105">Attributes</span></span>  
 <span data-ttu-id="306db-106">無。</span><span class="sxs-lookup"><span data-stu-id="306db-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="306db-107">子元素</span><span class="sxs-lookup"><span data-stu-id="306db-107">Child Elements</span></span>  
  
|<span data-ttu-id="306db-108">元素</span><span class="sxs-lookup"><span data-stu-id="306db-108">Element</span></span>|<span data-ttu-id="306db-109">描述</span><span class="sxs-lookup"><span data-stu-id="306db-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="306db-110">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="306db-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="306db-111">父項目</span><span class="sxs-lookup"><span data-stu-id="306db-111">Parent Elements</span></span>  
  
|<span data-ttu-id="306db-112">元素</span><span class="sxs-lookup"><span data-stu-id="306db-112">Element</span></span>|<span data-ttu-id="306db-113">描述</span><span class="sxs-lookup"><span data-stu-id="306db-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="306db-114">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="306db-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="306db-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="306db-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
