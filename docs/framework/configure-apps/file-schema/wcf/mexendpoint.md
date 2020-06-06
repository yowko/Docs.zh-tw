---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855105"
---
# \<mexEndpoint>
<span data-ttu-id="87598-101">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="87598-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="87598-102">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="87598-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="87598-103">語法</span><span class="sxs-lookup"><span data-stu-id="87598-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87598-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87598-104">Attributes and Elements</span></span>  
 <span data-ttu-id="87598-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="87598-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87598-106">屬性</span><span class="sxs-lookup"><span data-stu-id="87598-106">Attributes</span></span>  
  
|<span data-ttu-id="87598-107">屬性</span><span class="sxs-lookup"><span data-stu-id="87598-107">Attribute</span></span>|<span data-ttu-id="87598-108">描述</span><span class="sxs-lookup"><span data-stu-id="87598-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87598-109">NAME</span><span class="sxs-lookup"><span data-stu-id="87598-109">name</span></span>|<span data-ttu-id="87598-110">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="87598-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="87598-111">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="87598-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87598-112">子元素</span><span class="sxs-lookup"><span data-stu-id="87598-112">Child Elements</span></span>  
 <span data-ttu-id="87598-113">無。</span><span class="sxs-lookup"><span data-stu-id="87598-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87598-114">父項目</span><span class="sxs-lookup"><span data-stu-id="87598-114">Parent Elements</span></span>  
  
|<span data-ttu-id="87598-115">元素</span><span class="sxs-lookup"><span data-stu-id="87598-115">Element</span></span>|<span data-ttu-id="87598-116">描述</span><span class="sxs-lookup"><span data-stu-id="87598-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="87598-117">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="87598-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
