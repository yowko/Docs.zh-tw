---
title: "&lt;contractTypeNames&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bebea15e6d1f24c95905355dbced33aa9c5150f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="e1aa3-102">&lt;contractTypeNames&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="e1aa3-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="e1aa3-103">組態項目，這個項目會指定要搜尋之服務的合約名稱，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="e1aa3-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="e1aa3-105">請注意，在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 中，一個端點僅支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="e1aa3-106">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e1aa3-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="e1aa3-107">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="e1aa3-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1aa3-108">語法</span><span class="sxs-lookup"><span data-stu-id="e1aa3-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1aa3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1aa3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1aa3-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1aa3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e1aa3-111">Attributes</span></span>  
  
|<span data-ttu-id="e1aa3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e1aa3-112">Attribute</span></span>|<span data-ttu-id="e1aa3-113">描述</span><span class="sxs-lookup"><span data-stu-id="e1aa3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1aa3-114">name</span><span class="sxs-lookup"><span data-stu-id="e1aa3-114">name</span></span>|<span data-ttu-id="e1aa3-115">指定合約型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="e1aa3-116">namespace</span><span class="sxs-lookup"><span data-stu-id="e1aa3-116">namespace</span></span>|<span data-ttu-id="e1aa3-117">指定合約型別命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1aa3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="e1aa3-118">Child Elements</span></span>  
 <span data-ttu-id="e1aa3-119">無</span><span class="sxs-lookup"><span data-stu-id="e1aa3-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1aa3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e1aa3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1aa3-121">項目</span><span class="sxs-lookup"><span data-stu-id="e1aa3-121">Element</span></span>|<span data-ttu-id="e1aa3-122">說明</span><span class="sxs-lookup"><span data-stu-id="e1aa3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1aa3-123">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="e1aa3-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="e1aa3-124">合約型別名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1aa3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1aa3-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
