---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75886c08d3e358d4ed6d3d3048594ef28f06a7af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="191e0-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="191e0-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="191e0-103">這個組態項目會定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="191e0-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="191e0-104">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="191e0-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="191e0-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="191e0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="191e0-106">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="191e0-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191e0-107">語法</span><span class="sxs-lookup"><span data-stu-id="191e0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="191e0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="191e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="191e0-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="191e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="191e0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="191e0-110">Attributes</span></span>  
  
|<span data-ttu-id="191e0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="191e0-111">Attribute</span></span>|<span data-ttu-id="191e0-112">描述</span><span class="sxs-lookup"><span data-stu-id="191e0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="191e0-113">name</span><span class="sxs-lookup"><span data-stu-id="191e0-113">name</span></span>|<span data-ttu-id="191e0-114">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="191e0-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="191e0-115">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="191e0-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="191e0-116">子元素</span><span class="sxs-lookup"><span data-stu-id="191e0-116">Child Elements</span></span>  
 <span data-ttu-id="191e0-117">無。</span><span class="sxs-lookup"><span data-stu-id="191e0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="191e0-118">父項目</span><span class="sxs-lookup"><span data-stu-id="191e0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="191e0-119">項目</span><span class="sxs-lookup"><span data-stu-id="191e0-119">Element</span></span>|<span data-ttu-id="191e0-120">說明</span><span class="sxs-lookup"><span data-stu-id="191e0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="191e0-121">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="191e0-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="191e0-122">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="191e0-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
