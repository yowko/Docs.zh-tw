---
title: '&lt;服務&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: a48bd0ac30c1a85602122b2fd9213c2aa5159e91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148093"
---
# <a name="ltservicesgt"></a><span data-ttu-id="26a5e-102">&lt;服務&gt;</span><span class="sxs-lookup"><span data-stu-id="26a5e-102">&lt;services&gt;</span></span>
<span data-ttu-id="26a5e-103">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="26a5e-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="26a5e-104">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="26a5e-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="26a5e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="26a5e-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a5e-106">語法</span><span class="sxs-lookup"><span data-stu-id="26a5e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26a5e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="26a5e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="26a5e-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="26a5e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26a5e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="26a5e-109">Attributes</span></span>  
 <span data-ttu-id="26a5e-110">無</span><span class="sxs-lookup"><span data-stu-id="26a5e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="26a5e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="26a5e-111">Child Elements</span></span>  
  
|<span data-ttu-id="26a5e-112">項目</span><span class="sxs-lookup"><span data-stu-id="26a5e-112">Element</span></span>|<span data-ttu-id="26a5e-113">描述</span><span class="sxs-lookup"><span data-stu-id="26a5e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26a5e-114">\<service></span><span class="sxs-lookup"><span data-stu-id="26a5e-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="26a5e-115">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="26a5e-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26a5e-116">父項目</span><span class="sxs-lookup"><span data-stu-id="26a5e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="26a5e-117">項目</span><span class="sxs-lookup"><span data-stu-id="26a5e-117">Element</span></span>|<span data-ttu-id="26a5e-118">描述</span><span class="sxs-lookup"><span data-stu-id="26a5e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26a5e-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26a5e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="26a5e-120">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="26a5e-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26a5e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a5e-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
