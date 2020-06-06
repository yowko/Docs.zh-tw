---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854987"
---
# \<services>
<span data-ttu-id="3ce3f-101">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="3ce3f-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ce3f-102">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="3ce3f-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="3ce3f-103">語法</span><span class="sxs-lookup"><span data-stu-id="3ce3f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce3f-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ce3f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3ce3f-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ce3f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce3f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3ce3f-106">Attributes</span></span>  
 <span data-ttu-id="3ce3f-107">無</span><span class="sxs-lookup"><span data-stu-id="3ce3f-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ce3f-108">子元素</span><span class="sxs-lookup"><span data-stu-id="3ce3f-108">Child Elements</span></span>  
  
|<span data-ttu-id="3ce3f-109">元素</span><span class="sxs-lookup"><span data-stu-id="3ce3f-109">Element</span></span>|<span data-ttu-id="3ce3f-110">描述</span><span class="sxs-lookup"><span data-stu-id="3ce3f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="3ce3f-111">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="3ce3f-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ce3f-112">父項目</span><span class="sxs-lookup"><span data-stu-id="3ce3f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce3f-113">元素</span><span class="sxs-lookup"><span data-stu-id="3ce3f-113">Element</span></span>|<span data-ttu-id="3ce3f-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ce3f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="3ce3f-115">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="3ce3f-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ce3f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce3f-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
