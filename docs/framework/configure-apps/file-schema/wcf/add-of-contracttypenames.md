---
title: <add> 的 <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 69a0bbbc8774251dbdc062875bb06453f355c882
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149136"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="89f3f-102">\<add> 的 \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="89f3f-102">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="89f3f-103">組態項目，這個項目會指定要搜尋之服務的合約名稱，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="89f3f-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="89f3f-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="89f3f-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="89f3f-105">請注意，在 Windows Communication Foundation (WCF) 中，端點只能支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="89f3f-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="89f3f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="89f3f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89f3f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89f3f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="89f3f-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="89f3f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89f3f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="89f3f-109">Attributes</span></span>  
  
|<span data-ttu-id="89f3f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="89f3f-110">Attribute</span></span>|<span data-ttu-id="89f3f-111">描述</span><span class="sxs-lookup"><span data-stu-id="89f3f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89f3f-112">NAME</span><span class="sxs-lookup"><span data-stu-id="89f3f-112">name</span></span>|<span data-ttu-id="89f3f-113">指定合約型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="89f3f-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="89f3f-114">namespace</span><span class="sxs-lookup"><span data-stu-id="89f3f-114">namespace</span></span>|<span data-ttu-id="89f3f-115">指定合約型別命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="89f3f-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89f3f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="89f3f-116">Child Elements</span></span>  

 <span data-ttu-id="89f3f-117">無</span><span class="sxs-lookup"><span data-stu-id="89f3f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89f3f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="89f3f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="89f3f-119">項目</span><span class="sxs-lookup"><span data-stu-id="89f3f-119">Element</span></span>|<span data-ttu-id="89f3f-120">描述</span><span class="sxs-lookup"><span data-stu-id="89f3f-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="89f3f-121">合約型別名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="89f3f-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89f3f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89f3f-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
