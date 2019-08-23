---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919510"
---
# <a name="clientvia"></a><span data-ttu-id="4712b-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="4712b-101">\<clientVia></span></span>
<span data-ttu-id="4712b-102">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="4712b-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="4712b-103">如需詳細資訊，請參閱 <xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="4712b-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="4712b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4712b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4712b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4712b-105">\<behaviors></span></span>  
<span data-ttu-id="4712b-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4712b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4712b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4712b-107">\<behavior></span></span>  
<span data-ttu-id="4712b-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="4712b-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4712b-109">語法</span><span class="sxs-lookup"><span data-stu-id="4712b-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4712b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4712b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4712b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4712b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4712b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4712b-112">Attributes</span></span>  
  
|<span data-ttu-id="4712b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4712b-113">Attribute</span></span>|<span data-ttu-id="4712b-114">描述</span><span class="sxs-lookup"><span data-stu-id="4712b-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="4712b-115">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="4712b-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4712b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="4712b-116">Child Elements</span></span>  
 <span data-ttu-id="4712b-117">None</span><span class="sxs-lookup"><span data-stu-id="4712b-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4712b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="4712b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4712b-119">項目</span><span class="sxs-lookup"><span data-stu-id="4712b-119">Element</span></span>|<span data-ttu-id="4712b-120">描述</span><span class="sxs-lookup"><span data-stu-id="4712b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4712b-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4712b-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4712b-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="4712b-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4712b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4712b-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
