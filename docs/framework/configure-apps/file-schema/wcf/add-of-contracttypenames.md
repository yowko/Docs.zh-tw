---
title: <add> 的 <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091313"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="2ceea-102">\<add> of \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="2ceea-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="2ceea-103">組態項目，這個項目會指定要搜尋之服務的合約名稱，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="2ceea-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="2ceea-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="2ceea-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="2ceea-105">請注意，在 Windows Communication Foundation (WCF) 端點僅支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="2ceea-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="2ceea-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2ceea-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ceea-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2ceea-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ceea-108">語法</span><span class="sxs-lookup"><span data-stu-id="2ceea-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ceea-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2ceea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ceea-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2ceea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ceea-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2ceea-111">Attributes</span></span>  
  
|<span data-ttu-id="2ceea-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2ceea-112">Attribute</span></span>|<span data-ttu-id="2ceea-113">描述</span><span class="sxs-lookup"><span data-stu-id="2ceea-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ceea-114">名稱</span><span class="sxs-lookup"><span data-stu-id="2ceea-114">name</span></span>|<span data-ttu-id="2ceea-115">指定合約型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="2ceea-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="2ceea-116">namespace</span><span class="sxs-lookup"><span data-stu-id="2ceea-116">namespace</span></span>|<span data-ttu-id="2ceea-117">指定合約型別命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="2ceea-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ceea-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2ceea-118">Child Elements</span></span>  
 <span data-ttu-id="2ceea-119">None</span><span class="sxs-lookup"><span data-stu-id="2ceea-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ceea-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2ceea-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2ceea-121">項目</span><span class="sxs-lookup"><span data-stu-id="2ceea-121">Element</span></span>|<span data-ttu-id="2ceea-122">描述</span><span class="sxs-lookup"><span data-stu-id="2ceea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ceea-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="2ceea-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="2ceea-124">合約型別名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="2ceea-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ceea-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ceea-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
