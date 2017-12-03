---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6d2940a4c4615a922efcc74802a82adbe10267c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="79b70-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="79b70-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="79b70-103">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="79b70-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="79b70-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="79b70-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79b70-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="79b70-105">\<behaviors></span></span>  
<span data-ttu-id="79b70-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="79b70-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79b70-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="79b70-107">\<behavior></span></span>  
<span data-ttu-id="79b70-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="79b70-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b70-109">語法</span><span class="sxs-lookup"><span data-stu-id="79b70-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="79b70-110">類型</span><span class="sxs-lookup"><span data-stu-id="79b70-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79b70-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79b70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="79b70-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="79b70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79b70-113">屬性</span><span class="sxs-lookup"><span data-stu-id="79b70-113">Attributes</span></span>  
  
|<span data-ttu-id="79b70-114">屬性</span><span class="sxs-lookup"><span data-stu-id="79b70-114">Attribute</span></span>|<span data-ttu-id="79b70-115">描述</span><span class="sxs-lookup"><span data-stu-id="79b70-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="79b70-116"><xref:System.TimeSpan> 值，指定交易必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="79b70-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="79b70-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="79b70-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79b70-118">子元素</span><span class="sxs-lookup"><span data-stu-id="79b70-118">Child Elements</span></span>  
 <span data-ttu-id="79b70-119">無。</span><span class="sxs-lookup"><span data-stu-id="79b70-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79b70-120">父項目</span><span class="sxs-lookup"><span data-stu-id="79b70-120">Parent Elements</span></span>  
  
|<span data-ttu-id="79b70-121">項目</span><span class="sxs-lookup"><span data-stu-id="79b70-121">Element</span></span>|<span data-ttu-id="79b70-122">說明</span><span class="sxs-lookup"><span data-stu-id="79b70-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79b70-123">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="79b70-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="79b70-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="79b70-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79b70-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b70-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
