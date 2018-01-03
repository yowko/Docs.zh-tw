---
title: "&lt;逾時&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04003584cf12355116d32cccffdcb2b9990b1b85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="b23ad-102">&lt;逾時&gt;</span><span class="sxs-lookup"><span data-stu-id="b23ad-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="b23ad-103">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b23ad-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="b23ad-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b23ad-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b23ad-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="b23ad-105">\<client></span></span>  
<span data-ttu-id="b23ad-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="b23ad-106">\<endpoint></span></span>  
<span data-ttu-id="b23ad-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="b23ad-107">\<host></span></span>  
<span data-ttu-id="b23ad-108">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="b23ad-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23ad-109">語法</span><span class="sxs-lookup"><span data-stu-id="b23ad-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b23ad-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b23ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b23ad-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b23ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b23ad-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b23ad-112">Attributes</span></span>  
  
|<span data-ttu-id="b23ad-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b23ad-113">Attribute</span></span>|<span data-ttu-id="b23ad-114">描述</span><span class="sxs-lookup"><span data-stu-id="b23ad-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b23ad-115"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b23ad-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="b23ad-116"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b23ad-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b23ad-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b23ad-117">Child Elements</span></span>  
 <span data-ttu-id="b23ad-118">無。</span><span class="sxs-lookup"><span data-stu-id="b23ad-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b23ad-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b23ad-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b23ad-120">項目</span><span class="sxs-lookup"><span data-stu-id="b23ad-120">Element</span></span>|<span data-ttu-id="b23ad-121">描述</span><span class="sxs-lookup"><span data-stu-id="b23ad-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b23ad-122">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="b23ad-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="b23ad-123">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="b23ad-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b23ad-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="b23ad-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="b23ad-125">裝載</span><span class="sxs-lookup"><span data-stu-id="b23ad-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
