---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 2c3f501f44d9e3c601e654041eb9d5a7de8a0a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626767"
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="b23b5-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="b23b5-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="b23b5-103">組態區段，這個區段會指定合約型別名稱清單 (要搜尋之服務的合約名稱)，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="b23b5-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="b23b5-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="b23b5-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="b23b5-105">請注意，在 Windows Communication Foundation (WCF) 端點僅支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="b23b5-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="b23b5-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b23b5-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="b23b5-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b23b5-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23b5-108">語法</span><span class="sxs-lookup"><span data-stu-id="b23b5-108">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b23b5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b23b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b23b5-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b23b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b23b5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b23b5-111">Attributes</span></span>  
 <span data-ttu-id="b23b5-112">無。</span><span class="sxs-lookup"><span data-stu-id="b23b5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b23b5-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b23b5-113">Child Elements</span></span>  
  
|<span data-ttu-id="b23b5-114">項目</span><span class="sxs-lookup"><span data-stu-id="b23b5-114">Element</span></span>|<span data-ttu-id="b23b5-115">描述</span><span class="sxs-lookup"><span data-stu-id="b23b5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b23b5-116">\<add></span><span class="sxs-lookup"><span data-stu-id="b23b5-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="b23b5-117">合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="b23b5-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b23b5-118">父項目</span><span class="sxs-lookup"><span data-stu-id="b23b5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b23b5-119">項目</span><span class="sxs-lookup"><span data-stu-id="b23b5-119">Element</span></span>|<span data-ttu-id="b23b5-120">描述</span><span class="sxs-lookup"><span data-stu-id="b23b5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b23b5-121">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="b23b5-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="b23b5-122">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="b23b5-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="b23b5-123">準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。</span><span class="sxs-lookup"><span data-stu-id="b23b5-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b23b5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b23b5-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
