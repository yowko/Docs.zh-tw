---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b69b7d633fd99728936070e94da964e16de58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="4066b-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="4066b-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="4066b-103">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="4066b-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="4066b-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4066b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4066b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4066b-105">\<behaviors></span></span>  
<span data-ttu-id="4066b-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4066b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4066b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4066b-107">\<behavior></span></span>  
<span data-ttu-id="4066b-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="4066b-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4066b-109">語法</span><span class="sxs-lookup"><span data-stu-id="4066b-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="4066b-110">類型</span><span class="sxs-lookup"><span data-stu-id="4066b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4066b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4066b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4066b-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4066b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4066b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4066b-113">Attributes</span></span>  
  
|<span data-ttu-id="4066b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="4066b-114">Attribute</span></span>|<span data-ttu-id="4066b-115">描述</span><span class="sxs-lookup"><span data-stu-id="4066b-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="4066b-116"><xref:System.TimeSpan> 值，指定交易必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4066b-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="4066b-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="4066b-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4066b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="4066b-118">Child Elements</span></span>  
 <span data-ttu-id="4066b-119">無。</span><span class="sxs-lookup"><span data-stu-id="4066b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4066b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4066b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4066b-121">項目</span><span class="sxs-lookup"><span data-stu-id="4066b-121">Element</span></span>|<span data-ttu-id="4066b-122">說明</span><span class="sxs-lookup"><span data-stu-id="4066b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4066b-123">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4066b-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4066b-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="4066b-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4066b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4066b-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
