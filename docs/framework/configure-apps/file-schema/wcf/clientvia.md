---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 48e56b79f47e84122ddd4d7f55d50044510bfa66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149048"
---
# <a name="ltclientviagt"></a><span data-ttu-id="3424a-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="3424a-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="3424a-103">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="3424a-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="3424a-104">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="3424a-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="3424a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3424a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3424a-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3424a-106">\<behaviors></span></span>  
<span data-ttu-id="3424a-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3424a-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="3424a-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3424a-108">\<behavior></span></span>  
<span data-ttu-id="3424a-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="3424a-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3424a-110">語法</span><span class="sxs-lookup"><span data-stu-id="3424a-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3424a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3424a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3424a-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3424a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3424a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3424a-113">Attributes</span></span>  
  
|<span data-ttu-id="3424a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="3424a-114">Attribute</span></span>|<span data-ttu-id="3424a-115">描述</span><span class="sxs-lookup"><span data-stu-id="3424a-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="3424a-116">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="3424a-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3424a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="3424a-117">Child Elements</span></span>  
 <span data-ttu-id="3424a-118">無</span><span class="sxs-lookup"><span data-stu-id="3424a-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3424a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3424a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3424a-120">項目</span><span class="sxs-lookup"><span data-stu-id="3424a-120">Element</span></span>|<span data-ttu-id="3424a-121">描述</span><span class="sxs-lookup"><span data-stu-id="3424a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3424a-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3424a-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3424a-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="3424a-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3424a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3424a-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
