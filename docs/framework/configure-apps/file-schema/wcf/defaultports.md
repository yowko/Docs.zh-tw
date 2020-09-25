---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192369"
---
# \<defaultPorts>

<span data-ttu-id="57e62-101">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="57e62-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="57e62-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="57e62-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57e62-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57e62-103">Attributes and Elements</span></span>  

 <span data-ttu-id="57e62-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="57e62-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57e62-105">屬性</span><span class="sxs-lookup"><span data-stu-id="57e62-105">Attributes</span></span>  

 <span data-ttu-id="57e62-106">無。</span><span class="sxs-lookup"><span data-stu-id="57e62-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57e62-107">子元素</span><span class="sxs-lookup"><span data-stu-id="57e62-107">Child Elements</span></span>  
  
|<span data-ttu-id="57e62-108">項目</span><span class="sxs-lookup"><span data-stu-id="57e62-108">Element</span></span>|<span data-ttu-id="57e62-109">描述</span><span class="sxs-lookup"><span data-stu-id="57e62-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57e62-110">\<add> 次數 \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="57e62-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="57e62-111">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="57e62-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57e62-112">父項目</span><span class="sxs-lookup"><span data-stu-id="57e62-112">Parent Elements</span></span>  
  
|<span data-ttu-id="57e62-113">項目</span><span class="sxs-lookup"><span data-stu-id="57e62-113">Element</span></span>|<span data-ttu-id="57e62-114">描述</span><span class="sxs-lookup"><span data-stu-id="57e62-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="57e62-115">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="57e62-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57e62-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57e62-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
