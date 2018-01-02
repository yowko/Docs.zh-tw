---
title: '&lt;a d d&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5ac3a4af54d9f470a1cbd50096731b23d28b0c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="39f15-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="39f15-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="39f15-103">組態區段，這個區段會指定合約型別名稱清單 (要搜尋之服務的合約名稱)，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="39f15-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="39f15-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="39f15-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="39f15-105">請注意，在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 中，一個端點僅支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="39f15-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="39f15-106">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39f15-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="39f15-107">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="39f15-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f15-108">語法</span><span class="sxs-lookup"><span data-stu-id="39f15-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" 
                        maxResults="Integer" 
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f15-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39f15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="39f15-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39f15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f15-111">屬性</span><span class="sxs-lookup"><span data-stu-id="39f15-111">Attributes</span></span>  
 <span data-ttu-id="39f15-112">無。</span><span class="sxs-lookup"><span data-stu-id="39f15-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39f15-113">子元素</span><span class="sxs-lookup"><span data-stu-id="39f15-113">Child Elements</span></span>  
  
|<span data-ttu-id="39f15-114">項目</span><span class="sxs-lookup"><span data-stu-id="39f15-114">Element</span></span>|<span data-ttu-id="39f15-115">描述</span><span class="sxs-lookup"><span data-stu-id="39f15-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f15-116">\<add></span><span class="sxs-lookup"><span data-stu-id="39f15-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="39f15-117">合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="39f15-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39f15-118">父項目</span><span class="sxs-lookup"><span data-stu-id="39f15-118">Parent Elements</span></span>  
  
|<span data-ttu-id="39f15-119">項目</span><span class="sxs-lookup"><span data-stu-id="39f15-119">Element</span></span>|<span data-ttu-id="39f15-120">描述</span><span class="sxs-lookup"><span data-stu-id="39f15-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f15-121">\<n ></span><span class="sxs-lookup"><span data-stu-id="39f15-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="39f15-122">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="39f15-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="39f15-123">條件可以分組為搜尋準則 （指定您要尋找的服務），並且尋找終止準則 （搜尋應時間長短）。</span><span class="sxs-lookup"><span data-stu-id="39f15-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39f15-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="39f15-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
