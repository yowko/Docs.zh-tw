---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 5e3ca9c4a43432d7f5da6d8816b6a2b984851050
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177835"
---
# \<webScriptEndpoint>

<span data-ttu-id="2705e-101">這個設定元素會定義具有固定系結的標準端點，此系結 [\<webHttpBinding>](webhttpbinding.md) 會自動加入 [\<enableWebScript>](enablewebscript.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="2705e-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="2705e-102">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="2705e-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="2705e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2705e-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2705e-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2705e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2705e-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2705e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2705e-106">屬性</span><span class="sxs-lookup"><span data-stu-id="2705e-106">Attributes</span></span>  
  
|<span data-ttu-id="2705e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2705e-107">Attribute</span></span>|<span data-ttu-id="2705e-108">描述</span><span class="sxs-lookup"><span data-stu-id="2705e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2705e-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="2705e-109">webEndpointType</span></span>|<span data-ttu-id="2705e-110">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="2705e-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2705e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2705e-111">Child Elements</span></span>  

 <span data-ttu-id="2705e-112">無。</span><span class="sxs-lookup"><span data-stu-id="2705e-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2705e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="2705e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2705e-114">項目</span><span class="sxs-lookup"><span data-stu-id="2705e-114">Element</span></span>|<span data-ttu-id="2705e-115">描述</span><span class="sxs-lookup"><span data-stu-id="2705e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="2705e-116">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="2705e-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2705e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2705e-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
