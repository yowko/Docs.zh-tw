---
title: "&lt;主機&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d498190e7d7c3a6e879c50324e3b973f0f8e8fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="lthostgt"></a><span data-ttu-id="0605e-102">&lt;主機&gt;</span><span class="sxs-lookup"><span data-stu-id="0605e-102">&lt;host&gt;</span></span>
<span data-ttu-id="0605e-103">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="0605e-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="0605e-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0605e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0605e-105">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="0605e-105">\<services></span></span>  
<span data-ttu-id="0605e-106">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="0605e-106">\<service></span></span>  
<span data-ttu-id="0605e-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="0605e-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0605e-108">語法</span><span class="sxs-lookup"><span data-stu-id="0605e-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="0605e-109">類型</span><span class="sxs-lookup"><span data-stu-id="0605e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0605e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0605e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0605e-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0605e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0605e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0605e-112">Attributes</span></span>  
 <span data-ttu-id="0605e-113">無。</span><span class="sxs-lookup"><span data-stu-id="0605e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0605e-114">子項目</span><span class="sxs-lookup"><span data-stu-id="0605e-114">Child Elements</span></span>  
  
|<span data-ttu-id="0605e-115">項目</span><span class="sxs-lookup"><span data-stu-id="0605e-115">Element</span></span>|<span data-ttu-id="0605e-116">說明</span><span class="sxs-lookup"><span data-stu-id="0605e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0605e-117">\<s ></span><span class="sxs-lookup"><span data-stu-id="0605e-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="0605e-118">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="0605e-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="0605e-119">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="0605e-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="0605e-120">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0605e-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0605e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0605e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0605e-122">項目</span><span class="sxs-lookup"><span data-stu-id="0605e-122">Element</span></span>|<span data-ttu-id="0605e-123">說明</span><span class="sxs-lookup"><span data-stu-id="0605e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0605e-124">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="0605e-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="0605e-125">指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="0605e-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0605e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0605e-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="0605e-127">裝載</span><span class="sxs-lookup"><span data-stu-id="0605e-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
