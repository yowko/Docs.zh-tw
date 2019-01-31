---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 063dbee71a91e098e26026ea78c74642115c7955
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266659"
---
# <a name="clientvia"></a><span data-ttu-id="ccce9-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="ccce9-101">\<clientVia></span></span>
<span data-ttu-id="ccce9-102">指定應建立傳輸通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="ccce9-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ccce9-103">如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="ccce9-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="ccce9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccce9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccce9-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="ccce9-105">\<behaviors></span></span>  
<span data-ttu-id="ccce9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ccce9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ccce9-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ccce9-107">\<behavior></span></span>  
<span data-ttu-id="ccce9-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="ccce9-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccce9-109">語法</span><span class="sxs-lookup"><span data-stu-id="ccce9-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccce9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ccce9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ccce9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ccce9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccce9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ccce9-112">Attributes</span></span>  
  
|<span data-ttu-id="ccce9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ccce9-113">Attribute</span></span>|<span data-ttu-id="ccce9-114">描述</span><span class="sxs-lookup"><span data-stu-id="ccce9-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ccce9-115">字串，指定表示訊息應採用之路徑的 URI。</span><span class="sxs-lookup"><span data-stu-id="ccce9-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccce9-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ccce9-116">Child Elements</span></span>  
 <span data-ttu-id="ccce9-117">無</span><span class="sxs-lookup"><span data-stu-id="ccce9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccce9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ccce9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ccce9-119">項目</span><span class="sxs-lookup"><span data-stu-id="ccce9-119">Element</span></span>|<span data-ttu-id="ccce9-120">描述</span><span class="sxs-lookup"><span data-stu-id="ccce9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccce9-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ccce9-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ccce9-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="ccce9-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccce9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccce9-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
