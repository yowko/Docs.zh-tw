---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 9619c27c8c6d41250eeaeccabebe611e94b7d874
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769729"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="e45b4-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="e45b4-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="e45b4-102">此組態元素定義具有固定的標準端點[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)繫結，會自動加入[ \<Enablewebscript&gt >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)行為。</span><span class="sxs-lookup"><span data-stu-id="e45b4-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="e45b4-103">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="e45b4-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="e45b4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e45b4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e45b4-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e45b4-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="e45b4-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e45b4-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e45b4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e45b4-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e45b4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e45b4-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e45b4-109">Attributes</span></span>  
  
|<span data-ttu-id="e45b4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e45b4-110">Attribute</span></span>|<span data-ttu-id="e45b4-111">描述</span><span class="sxs-lookup"><span data-stu-id="e45b4-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e45b4-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e45b4-112">webEndpointType</span></span>|<span data-ttu-id="e45b4-113">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="e45b4-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e45b4-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e45b4-114">Child Elements</span></span>  
 <span data-ttu-id="e45b4-115">無。</span><span class="sxs-lookup"><span data-stu-id="e45b4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e45b4-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e45b4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e45b4-117">項目</span><span class="sxs-lookup"><span data-stu-id="e45b4-117">Element</span></span>|<span data-ttu-id="e45b4-118">描述</span><span class="sxs-lookup"><span data-stu-id="e45b4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e45b4-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e45b4-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e45b4-120">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="e45b4-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e45b4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e45b4-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
