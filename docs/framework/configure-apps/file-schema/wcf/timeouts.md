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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="9edb4-102">&lt;逾時&gt;</span><span class="sxs-lookup"><span data-stu-id="9edb4-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="9edb4-103">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9edb4-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="9edb4-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9edb4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9edb4-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="9edb4-105">\<client></span></span>  
<span data-ttu-id="9edb4-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="9edb4-106">\<endpoint></span></span>  
<span data-ttu-id="9edb4-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="9edb4-107">\<host></span></span>  
<span data-ttu-id="9edb4-108">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="9edb4-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9edb4-109">語法</span><span class="sxs-lookup"><span data-stu-id="9edb4-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9edb4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9edb4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9edb4-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9edb4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9edb4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9edb4-112">Attributes</span></span>  
  
|<span data-ttu-id="9edb4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9edb4-113">Attribute</span></span>|<span data-ttu-id="9edb4-114">描述</span><span class="sxs-lookup"><span data-stu-id="9edb4-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9edb4-115"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9edb4-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="9edb4-116"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9edb4-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9edb4-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9edb4-117">Child Elements</span></span>  
 <span data-ttu-id="9edb4-118">無。</span><span class="sxs-lookup"><span data-stu-id="9edb4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9edb4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9edb4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9edb4-120">項目</span><span class="sxs-lookup"><span data-stu-id="9edb4-120">Element</span></span>|<span data-ttu-id="9edb4-121">說明</span><span class="sxs-lookup"><span data-stu-id="9edb4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9edb4-122">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="9edb4-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="9edb4-123">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="9edb4-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9edb4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9edb4-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="9edb4-125">裝載</span><span class="sxs-lookup"><span data-stu-id="9edb4-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
