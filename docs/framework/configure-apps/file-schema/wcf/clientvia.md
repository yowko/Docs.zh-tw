---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398115"
---
# \<clientVia>
<span data-ttu-id="19ca0-101">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="19ca0-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="19ca0-102">如需詳細資訊，請參閱 <xref:System.ServiceModel.Description.ClientViaBehavior> 。</span><span class="sxs-lookup"><span data-stu-id="19ca0-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="19ca0-103">語法</span><span class="sxs-lookup"><span data-stu-id="19ca0-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19ca0-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19ca0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="19ca0-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19ca0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19ca0-106">屬性</span><span class="sxs-lookup"><span data-stu-id="19ca0-106">Attributes</span></span>  
  
|<span data-ttu-id="19ca0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="19ca0-107">Attribute</span></span>|<span data-ttu-id="19ca0-108">描述</span><span class="sxs-lookup"><span data-stu-id="19ca0-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="19ca0-109">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="19ca0-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19ca0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="19ca0-110">Child Elements</span></span>  
 <span data-ttu-id="19ca0-111">無</span><span class="sxs-lookup"><span data-stu-id="19ca0-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19ca0-112">父項目</span><span class="sxs-lookup"><span data-stu-id="19ca0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="19ca0-113">元素</span><span class="sxs-lookup"><span data-stu-id="19ca0-113">Element</span></span>|<span data-ttu-id="19ca0-114">描述</span><span class="sxs-lookup"><span data-stu-id="19ca0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="19ca0-115">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="19ca0-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19ca0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19ca0-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
