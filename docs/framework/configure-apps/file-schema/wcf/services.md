---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854987"
---
# <a name="services"></a><span data-ttu-id="c9c57-101">\<services></span><span class="sxs-lookup"><span data-stu-id="c9c57-101">\<services></span></span>
<span data-ttu-id="c9c57-102">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="c9c57-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="c9c57-103">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="c9c57-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="c9c57-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c9c57-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c9c57-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c9c57-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c9c57-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<服務 >**</span><span class="sxs-lookup"><span data-stu-id="c9c57-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c57-107">語法</span><span class="sxs-lookup"><span data-stu-id="c9c57-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c57-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9c57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c57-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9c57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c57-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c9c57-110">Attributes</span></span>  
 <span data-ttu-id="c9c57-111">None</span><span class="sxs-lookup"><span data-stu-id="c9c57-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9c57-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c9c57-112">Child Elements</span></span>  
  
|<span data-ttu-id="c9c57-113">項目</span><span class="sxs-lookup"><span data-stu-id="c9c57-113">Element</span></span>|<span data-ttu-id="c9c57-114">說明</span><span class="sxs-lookup"><span data-stu-id="c9c57-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c57-115">\<service></span><span class="sxs-lookup"><span data-stu-id="c9c57-115">\<service></span></span>](service.md)|<span data-ttu-id="c9c57-116">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="c9c57-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c57-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c9c57-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c57-118">項目</span><span class="sxs-lookup"><span data-stu-id="c9c57-118">Element</span></span>|<span data-ttu-id="c9c57-119">描述</span><span class="sxs-lookup"><span data-stu-id="c9c57-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c57-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9c57-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="c9c57-121">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="c9c57-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9c57-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9c57-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
