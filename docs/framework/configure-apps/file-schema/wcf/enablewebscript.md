---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919120"
---
# <a name="enablewebscript"></a><span data-ttu-id="5298e-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="5298e-101">\<enableWebScript></span></span>
<span data-ttu-id="5298e-102">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="5298e-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="5298e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5298e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5298e-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="5298e-104">\<behaviors></span></span>  
<span data-ttu-id="5298e-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5298e-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="5298e-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="5298e-106">\<behavior></span></span>  
<span data-ttu-id="5298e-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="5298e-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5298e-108">語法</span><span class="sxs-lookup"><span data-stu-id="5298e-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5298e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5298e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5298e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5298e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5298e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5298e-111">Attributes</span></span>  
 <span data-ttu-id="5298e-112">無。</span><span class="sxs-lookup"><span data-stu-id="5298e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5298e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5298e-113">Child Elements</span></span>  
 <span data-ttu-id="5298e-114">無。</span><span class="sxs-lookup"><span data-stu-id="5298e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5298e-115">父項目</span><span class="sxs-lookup"><span data-stu-id="5298e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5298e-116">項目</span><span class="sxs-lookup"><span data-stu-id="5298e-116">Element</span></span>|<span data-ttu-id="5298e-117">描述</span><span class="sxs-lookup"><span data-stu-id="5298e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5298e-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5298e-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5298e-119">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="5298e-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5298e-120">備註</span><span class="sxs-lookup"><span data-stu-id="5298e-120">Remarks</span></span>  
 <span data-ttu-id="5298e-121">這個行為只能與[ \<webHttpBinding >](webhttpbinding.md)標準系結或[ \<webMessageEncoding >](webmessageencoding.md)繫結項目搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5298e-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="5298e-122">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="5298e-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5298e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5298e-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="5298e-124">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="5298e-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="5298e-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="5298e-125">\<webHttp></span></span>](webhttp.md)
