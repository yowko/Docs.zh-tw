---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271690"
---
# <a name="mexendpoint"></a><span data-ttu-id="8cb51-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="8cb51-101">\<mexEndpoint></span></span>
<span data-ttu-id="8cb51-102">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="8cb51-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="8cb51-103">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="8cb51-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="8cb51-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cb51-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cb51-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8cb51-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb51-106">語法</span><span class="sxs-lookup"><span data-stu-id="8cb51-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cb51-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cb51-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8cb51-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8cb51-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cb51-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8cb51-109">Attributes</span></span>  
  
|<span data-ttu-id="8cb51-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8cb51-110">Attribute</span></span>|<span data-ttu-id="8cb51-111">描述</span><span class="sxs-lookup"><span data-stu-id="8cb51-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cb51-112">name</span><span class="sxs-lookup"><span data-stu-id="8cb51-112">name</span></span>|<span data-ttu-id="8cb51-113">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="8cb51-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="8cb51-114">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="8cb51-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cb51-115">子元素</span><span class="sxs-lookup"><span data-stu-id="8cb51-115">Child Elements</span></span>  
 <span data-ttu-id="8cb51-116">無。</span><span class="sxs-lookup"><span data-stu-id="8cb51-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cb51-117">父項目</span><span class="sxs-lookup"><span data-stu-id="8cb51-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8cb51-118">項目</span><span class="sxs-lookup"><span data-stu-id="8cb51-118">Element</span></span>|<span data-ttu-id="8cb51-119">描述</span><span class="sxs-lookup"><span data-stu-id="8cb51-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cb51-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8cb51-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="8cb51-121">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="8cb51-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
