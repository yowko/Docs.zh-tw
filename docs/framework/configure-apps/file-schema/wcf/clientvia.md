---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673624"
---
# <a name="clientvia"></a><span data-ttu-id="5569d-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="5569d-101">\<clientVia></span></span>
<span data-ttu-id="5569d-102">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="5569d-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="5569d-103">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="5569d-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="5569d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5569d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5569d-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5569d-105">\<behaviors></span></span>  
<span data-ttu-id="5569d-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5569d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5569d-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5569d-107">\<behavior></span></span>  
<span data-ttu-id="5569d-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="5569d-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5569d-109">語法</span><span class="sxs-lookup"><span data-stu-id="5569d-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5569d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5569d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5569d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5569d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5569d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5569d-112">Attributes</span></span>  
  
|<span data-ttu-id="5569d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5569d-113">Attribute</span></span>|<span data-ttu-id="5569d-114">描述</span><span class="sxs-lookup"><span data-stu-id="5569d-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="5569d-115">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="5569d-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5569d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5569d-116">Child Elements</span></span>  
 <span data-ttu-id="5569d-117">None</span><span class="sxs-lookup"><span data-stu-id="5569d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5569d-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5569d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5569d-119">項目</span><span class="sxs-lookup"><span data-stu-id="5569d-119">Element</span></span>|<span data-ttu-id="5569d-120">描述</span><span class="sxs-lookup"><span data-stu-id="5569d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5569d-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5569d-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5569d-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="5569d-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5569d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5569d-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
