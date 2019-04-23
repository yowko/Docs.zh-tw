---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168073"
---
# <a name="services"></a><span data-ttu-id="18139-101">\<services></span><span class="sxs-lookup"><span data-stu-id="18139-101">\<services></span></span>
<span data-ttu-id="18139-102">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="18139-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="18139-103">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="18139-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="18139-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18139-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18139-105">語法</span><span class="sxs-lookup"><span data-stu-id="18139-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18139-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18139-106">Attributes and Elements</span></span>  
 <span data-ttu-id="18139-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18139-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18139-108">屬性</span><span class="sxs-lookup"><span data-stu-id="18139-108">Attributes</span></span>  
 <span data-ttu-id="18139-109">None</span><span class="sxs-lookup"><span data-stu-id="18139-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18139-110">子元素</span><span class="sxs-lookup"><span data-stu-id="18139-110">Child Elements</span></span>  
  
|<span data-ttu-id="18139-111">項目</span><span class="sxs-lookup"><span data-stu-id="18139-111">Element</span></span>|<span data-ttu-id="18139-112">描述</span><span class="sxs-lookup"><span data-stu-id="18139-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18139-113">\<service></span><span class="sxs-lookup"><span data-stu-id="18139-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="18139-114">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="18139-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18139-115">父項目</span><span class="sxs-lookup"><span data-stu-id="18139-115">Parent Elements</span></span>  
  
|<span data-ttu-id="18139-116">項目</span><span class="sxs-lookup"><span data-stu-id="18139-116">Element</span></span>|<span data-ttu-id="18139-117">描述</span><span class="sxs-lookup"><span data-stu-id="18139-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18139-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="18139-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="18139-119">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="18139-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18139-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18139-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
