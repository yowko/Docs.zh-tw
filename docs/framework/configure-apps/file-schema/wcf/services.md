---
title: "&lt;服務&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="d1daa-102">&lt;服務&gt;</span><span class="sxs-lookup"><span data-stu-id="d1daa-102">&lt;services&gt;</span></span>
<span data-ttu-id="d1daa-103">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="d1daa-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d1daa-104">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="d1daa-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="d1daa-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d1daa-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1daa-106">語法</span><span class="sxs-lookup"><span data-stu-id="d1daa-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1daa-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1daa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d1daa-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1daa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1daa-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d1daa-109">Attributes</span></span>  
 <span data-ttu-id="d1daa-110">無</span><span class="sxs-lookup"><span data-stu-id="d1daa-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1daa-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d1daa-111">Child Elements</span></span>  
  
|<span data-ttu-id="d1daa-112">項目</span><span class="sxs-lookup"><span data-stu-id="d1daa-112">Element</span></span>|<span data-ttu-id="d1daa-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1daa-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1daa-114">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="d1daa-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="d1daa-115">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="d1daa-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1daa-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d1daa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d1daa-117">項目</span><span class="sxs-lookup"><span data-stu-id="d1daa-117">Element</span></span>|<span data-ttu-id="d1daa-118">描述</span><span class="sxs-lookup"><span data-stu-id="d1daa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1daa-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d1daa-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="d1daa-120">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="d1daa-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1daa-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1daa-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
