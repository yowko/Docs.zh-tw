---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: e8f0e0fa2ea1606bf980fd6fa1fcd47f12c3b540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204745"
---
# \<mexEndpoint>

<span data-ttu-id="0fbbc-101">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="0fbbc-102">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0fbbc-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0fbbc-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fbbc-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0fbbc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0fbbc-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fbbc-106">屬性</span><span class="sxs-lookup"><span data-stu-id="0fbbc-106">Attributes</span></span>  
  
|<span data-ttu-id="0fbbc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0fbbc-107">Attribute</span></span>|<span data-ttu-id="0fbbc-108">描述</span><span class="sxs-lookup"><span data-stu-id="0fbbc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fbbc-109">NAME</span><span class="sxs-lookup"><span data-stu-id="0fbbc-109">name</span></span>|<span data-ttu-id="0fbbc-110">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0fbbc-111">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fbbc-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0fbbc-112">Child Elements</span></span>  

 <span data-ttu-id="0fbbc-113">無。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fbbc-114">父項目</span><span class="sxs-lookup"><span data-stu-id="0fbbc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0fbbc-115">項目</span><span class="sxs-lookup"><span data-stu-id="0fbbc-115">Element</span></span>|<span data-ttu-id="0fbbc-116">描述</span><span class="sxs-lookup"><span data-stu-id="0fbbc-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0fbbc-117">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="0fbbc-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
