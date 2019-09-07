---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398115"
---
# <a name="clientvia"></a><span data-ttu-id="bc44d-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="bc44d-101">\<clientVia></span></span>
<span data-ttu-id="bc44d-102">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="bc44d-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="bc44d-103">如需詳細資訊，請參閱 <xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="bc44d-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="bc44d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc44d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc44d-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc44d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc44d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc44d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bc44d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc44d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc44d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc44d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc44d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientVia >**</span><span class="sxs-lookup"><span data-stu-id="bc44d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc44d-110">語法</span><span class="sxs-lookup"><span data-stu-id="bc44d-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc44d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc44d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc44d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc44d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc44d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bc44d-113">Attributes</span></span>  
  
|<span data-ttu-id="bc44d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="bc44d-114">Attribute</span></span>|<span data-ttu-id="bc44d-115">說明</span><span class="sxs-lookup"><span data-stu-id="bc44d-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="bc44d-116">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="bc44d-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc44d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="bc44d-117">Child Elements</span></span>  
 <span data-ttu-id="bc44d-118">無</span><span class="sxs-lookup"><span data-stu-id="bc44d-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc44d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bc44d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bc44d-120">項目</span><span class="sxs-lookup"><span data-stu-id="bc44d-120">Element</span></span>|<span data-ttu-id="bc44d-121">描述</span><span class="sxs-lookup"><span data-stu-id="bc44d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc44d-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bc44d-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bc44d-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="bc44d-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc44d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc44d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
