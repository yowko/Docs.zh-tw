---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855105"
---
# <a name="mexendpoint"></a><span data-ttu-id="64137-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="64137-101">\<mexEndpoint></span></span>
<span data-ttu-id="64137-102">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="64137-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="64137-103">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="64137-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="64137-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64137-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64137-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="64137-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="64137-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="64137-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="64137-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="64137-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64137-108">語法</span><span class="sxs-lookup"><span data-stu-id="64137-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64137-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="64137-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64137-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="64137-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64137-111">屬性</span><span class="sxs-lookup"><span data-stu-id="64137-111">Attributes</span></span>  
  
|<span data-ttu-id="64137-112">屬性</span><span class="sxs-lookup"><span data-stu-id="64137-112">Attribute</span></span>|<span data-ttu-id="64137-113">說明</span><span class="sxs-lookup"><span data-stu-id="64137-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64137-114">NAME</span><span class="sxs-lookup"><span data-stu-id="64137-114">name</span></span>|<span data-ttu-id="64137-115">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="64137-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="64137-116">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="64137-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64137-117">子元素</span><span class="sxs-lookup"><span data-stu-id="64137-117">Child Elements</span></span>  
 <span data-ttu-id="64137-118">無。</span><span class="sxs-lookup"><span data-stu-id="64137-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64137-119">父項目</span><span class="sxs-lookup"><span data-stu-id="64137-119">Parent Elements</span></span>  
  
|<span data-ttu-id="64137-120">項目</span><span class="sxs-lookup"><span data-stu-id="64137-120">Element</span></span>|<span data-ttu-id="64137-121">描述</span><span class="sxs-lookup"><span data-stu-id="64137-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64137-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="64137-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="64137-123">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="64137-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
