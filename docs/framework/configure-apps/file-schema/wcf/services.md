---
title: '&lt;服務&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749227"
---
# <a name="ltservicesgt"></a><span data-ttu-id="1619b-102">&lt;服務&gt;</span><span class="sxs-lookup"><span data-stu-id="1619b-102">&lt;services&gt;</span></span>
<span data-ttu-id="1619b-103">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="1619b-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="1619b-104">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="1619b-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="1619b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1619b-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1619b-106">語法</span><span class="sxs-lookup"><span data-stu-id="1619b-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1619b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1619b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1619b-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1619b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1619b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1619b-109">Attributes</span></span>  
 <span data-ttu-id="1619b-110">無</span><span class="sxs-lookup"><span data-stu-id="1619b-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1619b-111">子項目</span><span class="sxs-lookup"><span data-stu-id="1619b-111">Child Elements</span></span>  
  
|<span data-ttu-id="1619b-112">項目</span><span class="sxs-lookup"><span data-stu-id="1619b-112">Element</span></span>|<span data-ttu-id="1619b-113">描述</span><span class="sxs-lookup"><span data-stu-id="1619b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1619b-114">\<service></span><span class="sxs-lookup"><span data-stu-id="1619b-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="1619b-115">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="1619b-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1619b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="1619b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1619b-117">項目</span><span class="sxs-lookup"><span data-stu-id="1619b-117">Element</span></span>|<span data-ttu-id="1619b-118">描述</span><span class="sxs-lookup"><span data-stu-id="1619b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1619b-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1619b-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="1619b-120">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="1619b-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1619b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1619b-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
