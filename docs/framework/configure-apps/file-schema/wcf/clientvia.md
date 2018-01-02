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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a1870a8c331aae16ab14da62c64d6fb15ecd3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="6c2da-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="6c2da-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="6c2da-103">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="6c2da-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="6c2da-104">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="6c2da-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="6c2da-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6c2da-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c2da-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6c2da-106">\<behaviors></span></span>  
<span data-ttu-id="6c2da-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6c2da-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="6c2da-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6c2da-108">\<behavior></span></span>  
<span data-ttu-id="6c2da-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="6c2da-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2da-110">語法</span><span class="sxs-lookup"><span data-stu-id="6c2da-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c2da-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c2da-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6c2da-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6c2da-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c2da-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6c2da-113">Attributes</span></span>  
  
|<span data-ttu-id="6c2da-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6c2da-114">Attribute</span></span>|<span data-ttu-id="6c2da-115">描述</span><span class="sxs-lookup"><span data-stu-id="6c2da-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="6c2da-116">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="6c2da-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c2da-117">子元素</span><span class="sxs-lookup"><span data-stu-id="6c2da-117">Child Elements</span></span>  
 <span data-ttu-id="6c2da-118">無</span><span class="sxs-lookup"><span data-stu-id="6c2da-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c2da-119">父項目</span><span class="sxs-lookup"><span data-stu-id="6c2da-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6c2da-120">項目</span><span class="sxs-lookup"><span data-stu-id="6c2da-120">Element</span></span>|<span data-ttu-id="6c2da-121">描述</span><span class="sxs-lookup"><span data-stu-id="6c2da-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c2da-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6c2da-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6c2da-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="6c2da-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c2da-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2da-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
