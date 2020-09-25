---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: a323e6da0eb173e303d70cc3b7309b898a805573
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172810"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="8f226-101">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="8f226-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="8f226-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f226-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f226-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f226-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8f226-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8f226-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f226-105">屬性</span><span class="sxs-lookup"><span data-stu-id="8f226-105">Attributes</span></span>  

 <span data-ttu-id="8f226-106">無。</span><span class="sxs-lookup"><span data-stu-id="8f226-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f226-107">子元素</span><span class="sxs-lookup"><span data-stu-id="8f226-107">Child Elements</span></span>  
  
|<span data-ttu-id="8f226-108">項目</span><span class="sxs-lookup"><span data-stu-id="8f226-108">Element</span></span>|<span data-ttu-id="8f226-109">描述</span><span class="sxs-lookup"><span data-stu-id="8f226-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="8f226-110">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="8f226-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f226-111">父項目</span><span class="sxs-lookup"><span data-stu-id="8f226-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8f226-112">項目</span><span class="sxs-lookup"><span data-stu-id="8f226-112">Element</span></span>|<span data-ttu-id="8f226-113">描述</span><span class="sxs-lookup"><span data-stu-id="8f226-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8f226-114">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="8f226-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f226-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f226-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
