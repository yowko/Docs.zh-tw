---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854810"
---
# \<webScriptEndpoint>
<span data-ttu-id="779a2-101">此設定元素會定義具有固定系結的標準端點，此系結 [\<webHttpBinding>](webhttpbinding.md) 會自動新增 [\<enableWebScript>](enablewebscript.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="779a2-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="779a2-102">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="779a2-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="779a2-103">語法</span><span class="sxs-lookup"><span data-stu-id="779a2-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="779a2-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="779a2-104">Attributes and Elements</span></span>  
 <span data-ttu-id="779a2-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="779a2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="779a2-106">屬性</span><span class="sxs-lookup"><span data-stu-id="779a2-106">Attributes</span></span>  
  
|<span data-ttu-id="779a2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="779a2-107">Attribute</span></span>|<span data-ttu-id="779a2-108">描述</span><span class="sxs-lookup"><span data-stu-id="779a2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="779a2-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="779a2-109">webEndpointType</span></span>|<span data-ttu-id="779a2-110">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="779a2-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="779a2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="779a2-111">Child Elements</span></span>  
 <span data-ttu-id="779a2-112">無。</span><span class="sxs-lookup"><span data-stu-id="779a2-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="779a2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="779a2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="779a2-114">元素</span><span class="sxs-lookup"><span data-stu-id="779a2-114">Element</span></span>|<span data-ttu-id="779a2-115">描述</span><span class="sxs-lookup"><span data-stu-id="779a2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="779a2-116">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="779a2-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="779a2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="779a2-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
