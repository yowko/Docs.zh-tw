---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cdc85c23202154728610ab4721bf830004928c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="ef831-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="ef831-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="ef831-103">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="ef831-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ef831-104">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="ef831-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="ef831-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ef831-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef831-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ef831-106">\<behaviors></span></span>  
<span data-ttu-id="ef831-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ef831-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ef831-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ef831-108">\<behavior></span></span>  
<span data-ttu-id="ef831-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="ef831-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef831-110">語法</span><span class="sxs-lookup"><span data-stu-id="ef831-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef831-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ef831-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ef831-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ef831-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef831-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ef831-113">Attributes</span></span>  
  
|<span data-ttu-id="ef831-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ef831-114">Attribute</span></span>|<span data-ttu-id="ef831-115">描述</span><span class="sxs-lookup"><span data-stu-id="ef831-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ef831-116">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="ef831-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef831-117">子元素</span><span class="sxs-lookup"><span data-stu-id="ef831-117">Child Elements</span></span>  
 <span data-ttu-id="ef831-118">無</span><span class="sxs-lookup"><span data-stu-id="ef831-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef831-119">父項目</span><span class="sxs-lookup"><span data-stu-id="ef831-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef831-120">項目</span><span class="sxs-lookup"><span data-stu-id="ef831-120">Element</span></span>|<span data-ttu-id="ef831-121">說明</span><span class="sxs-lookup"><span data-stu-id="ef831-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef831-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ef831-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ef831-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="ef831-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef831-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef831-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
