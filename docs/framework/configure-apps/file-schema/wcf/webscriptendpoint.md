---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940411"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="08352-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="08352-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="08352-102">此設定元素會定義標準端點, 其中具有固定[ \<的 webHttpBinding >](webhttpbinding.md)系結[ \< ](enablewebscript.md) , 會自動新增 enableWebScript > 行為。</span><span class="sxs-lookup"><span data-stu-id="08352-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="08352-103">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="08352-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="08352-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="08352-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="08352-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="08352-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08352-106">語法</span><span class="sxs-lookup"><span data-stu-id="08352-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08352-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="08352-107">Attributes and Elements</span></span>  
 <span data-ttu-id="08352-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="08352-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08352-109">屬性</span><span class="sxs-lookup"><span data-stu-id="08352-109">Attributes</span></span>  
  
|<span data-ttu-id="08352-110">屬性</span><span class="sxs-lookup"><span data-stu-id="08352-110">Attribute</span></span>|<span data-ttu-id="08352-111">說明</span><span class="sxs-lookup"><span data-stu-id="08352-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08352-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="08352-112">webEndpointType</span></span>|<span data-ttu-id="08352-113">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="08352-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08352-114">子元素</span><span class="sxs-lookup"><span data-stu-id="08352-114">Child Elements</span></span>  
 <span data-ttu-id="08352-115">無。</span><span class="sxs-lookup"><span data-stu-id="08352-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08352-116">父項目</span><span class="sxs-lookup"><span data-stu-id="08352-116">Parent Elements</span></span>  
  
|<span data-ttu-id="08352-117">項目</span><span class="sxs-lookup"><span data-stu-id="08352-117">Element</span></span>|<span data-ttu-id="08352-118">描述</span><span class="sxs-lookup"><span data-stu-id="08352-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08352-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="08352-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="08352-120">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="08352-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08352-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08352-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
