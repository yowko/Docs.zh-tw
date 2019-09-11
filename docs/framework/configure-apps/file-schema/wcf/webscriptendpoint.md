---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854810"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="62827-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="62827-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="62827-102">此設定元素會定義標準端點，其中具有固定[ \<的 webHttpBinding >](webhttpbinding.md)系結[ \< ](enablewebscript.md) ，會自動新增 enableWebScript > 行為。</span><span class="sxs-lookup"><span data-stu-id="62827-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="62827-103">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="62827-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="62827-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62827-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62827-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62827-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62827-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="62827-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="62827-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webScriptEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="62827-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62827-108">語法</span><span class="sxs-lookup"><span data-stu-id="62827-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62827-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62827-109">Attributes and Elements</span></span>  
 <span data-ttu-id="62827-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="62827-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62827-111">屬性</span><span class="sxs-lookup"><span data-stu-id="62827-111">Attributes</span></span>  
  
|<span data-ttu-id="62827-112">屬性</span><span class="sxs-lookup"><span data-stu-id="62827-112">Attribute</span></span>|<span data-ttu-id="62827-113">說明</span><span class="sxs-lookup"><span data-stu-id="62827-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62827-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="62827-114">webEndpointType</span></span>|<span data-ttu-id="62827-115">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="62827-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62827-116">子元素</span><span class="sxs-lookup"><span data-stu-id="62827-116">Child Elements</span></span>  
 <span data-ttu-id="62827-117">無。</span><span class="sxs-lookup"><span data-stu-id="62827-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62827-118">父項目</span><span class="sxs-lookup"><span data-stu-id="62827-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62827-119">項目</span><span class="sxs-lookup"><span data-stu-id="62827-119">Element</span></span>|<span data-ttu-id="62827-120">描述</span><span class="sxs-lookup"><span data-stu-id="62827-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62827-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="62827-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="62827-122">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="62827-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62827-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62827-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
