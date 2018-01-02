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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc89a4b9735c13429b31d8cd7c5995f641afa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="ff9b3-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="ff9b3-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="ff9b3-103">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="ff9b3-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff9b3-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-105">\<behaviors></span></span>  
<span data-ttu-id="ff9b3-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ff9b3-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-107">\<behavior></span></span>  
<span data-ttu-id="ff9b3-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9b3-109">語法</span><span class="sxs-lookup"><span data-stu-id="ff9b3-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="ff9b3-110">類型</span><span class="sxs-lookup"><span data-stu-id="ff9b3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff9b3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff9b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ff9b3-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff9b3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ff9b3-113">Attributes</span></span>  
  
|<span data-ttu-id="ff9b3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ff9b3-114">Attribute</span></span>|<span data-ttu-id="ff9b3-115">描述</span><span class="sxs-lookup"><span data-stu-id="ff9b3-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="ff9b3-116"><xref:System.TimeSpan> 值，指定交易必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="ff9b3-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff9b3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ff9b3-118">Child Elements</span></span>  
 <span data-ttu-id="ff9b3-119">無。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff9b3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="ff9b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ff9b3-121">項目</span><span class="sxs-lookup"><span data-stu-id="ff9b3-121">Element</span></span>|<span data-ttu-id="ff9b3-122">描述</span><span class="sxs-lookup"><span data-stu-id="ff9b3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff9b3-123">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ff9b3-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff9b3-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff9b3-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="ff9b3-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
