---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 5e62201a38dc4dc251996531a4af5f294dd2395f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151099"
---
# \<clientVia>

<span data-ttu-id="53f32-101">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="53f32-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="53f32-102">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="53f32-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="53f32-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="53f32-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53f32-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53f32-104">Attributes and Elements</span></span>  

 <span data-ttu-id="53f32-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="53f32-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53f32-106">屬性</span><span class="sxs-lookup"><span data-stu-id="53f32-106">Attributes</span></span>  
  
|<span data-ttu-id="53f32-107">屬性</span><span class="sxs-lookup"><span data-stu-id="53f32-107">Attribute</span></span>|<span data-ttu-id="53f32-108">描述</span><span class="sxs-lookup"><span data-stu-id="53f32-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="53f32-109">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="53f32-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53f32-110">子元素</span><span class="sxs-lookup"><span data-stu-id="53f32-110">Child Elements</span></span>  

 <span data-ttu-id="53f32-111">無</span><span class="sxs-lookup"><span data-stu-id="53f32-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53f32-112">父項目</span><span class="sxs-lookup"><span data-stu-id="53f32-112">Parent Elements</span></span>  
  
|<span data-ttu-id="53f32-113">項目</span><span class="sxs-lookup"><span data-stu-id="53f32-113">Element</span></span>|<span data-ttu-id="53f32-114">描述</span><span class="sxs-lookup"><span data-stu-id="53f32-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="53f32-115">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="53f32-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53f32-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53f32-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
