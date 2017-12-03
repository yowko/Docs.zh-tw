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
ms.openlocfilehash: ca55770da8da0fe91a12aeb5fa72e61d6dcd67ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="ab963-102">&lt;服務&gt;</span><span class="sxs-lookup"><span data-stu-id="ab963-102">&lt;services&gt;</span></span>
<span data-ttu-id="ab963-103">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="ab963-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ab963-104">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="ab963-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="ab963-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ab963-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab963-106">語法</span><span class="sxs-lookup"><span data-stu-id="ab963-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab963-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab963-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ab963-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ab963-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab963-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ab963-109">Attributes</span></span>  
 <span data-ttu-id="ab963-110">無</span><span class="sxs-lookup"><span data-stu-id="ab963-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab963-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ab963-111">Child Elements</span></span>  
  
|<span data-ttu-id="ab963-112">項目</span><span class="sxs-lookup"><span data-stu-id="ab963-112">Element</span></span>|<span data-ttu-id="ab963-113">說明</span><span class="sxs-lookup"><span data-stu-id="ab963-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab963-114">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="ab963-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="ab963-115">定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="ab963-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab963-116">父項目</span><span class="sxs-lookup"><span data-stu-id="ab963-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ab963-117">項目</span><span class="sxs-lookup"><span data-stu-id="ab963-117">Element</span></span>|<span data-ttu-id="ab963-118">說明</span><span class="sxs-lookup"><span data-stu-id="ab963-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab963-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ab963-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="ab963-120">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="ab963-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab963-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab963-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
