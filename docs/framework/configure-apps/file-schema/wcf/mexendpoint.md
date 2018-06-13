---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: aceff3e373d9a5f7e57c28d85870af19ae8ef3e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747781"
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="9c4bf-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9c4bf-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="9c4bf-103">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="9c4bf-104">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="9c4bf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c4bf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c4bf-106">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="9c4bf-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4bf-107">語法</span><span class="sxs-lookup"><span data-stu-id="9c4bf-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c4bf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9c4bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9c4bf-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c4bf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9c4bf-110">Attributes</span></span>  
  
|<span data-ttu-id="9c4bf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9c4bf-111">Attribute</span></span>|<span data-ttu-id="9c4bf-112">描述</span><span class="sxs-lookup"><span data-stu-id="9c4bf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c4bf-113">name</span><span class="sxs-lookup"><span data-stu-id="9c4bf-113">name</span></span>|<span data-ttu-id="9c4bf-114">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="9c4bf-115">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c4bf-116">子項目</span><span class="sxs-lookup"><span data-stu-id="9c4bf-116">Child Elements</span></span>  
 <span data-ttu-id="9c4bf-117">無。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c4bf-118">父項目</span><span class="sxs-lookup"><span data-stu-id="9c4bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9c4bf-119">項目</span><span class="sxs-lookup"><span data-stu-id="9c4bf-119">Element</span></span>|<span data-ttu-id="9c4bf-120">描述</span><span class="sxs-lookup"><span data-stu-id="9c4bf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c4bf-121">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="9c4bf-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9c4bf-122">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="9c4bf-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
