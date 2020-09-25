---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: f1626983d34a7b66ee23c3a2d9a3c2107812e136
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175976"
---
# \<contractTypeNames>

<span data-ttu-id="9119a-101">組態區段，這個區段會指定合約型別名稱清單 (要搜尋之服務的合約名稱)，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="9119a-101">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="9119a-102">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="9119a-102">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="9119a-103">請注意，在 Windows Communication Foundation (WCF) 中，端點只能支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="9119a-103">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="9119a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9119a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9119a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9119a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9119a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9119a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9119a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9119a-107">Attributes</span></span>  

 <span data-ttu-id="9119a-108">無。</span><span class="sxs-lookup"><span data-stu-id="9119a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9119a-109">子元素</span><span class="sxs-lookup"><span data-stu-id="9119a-109">Child Elements</span></span>  
  
|<span data-ttu-id="9119a-110">項目</span><span class="sxs-lookup"><span data-stu-id="9119a-110">Element</span></span>|<span data-ttu-id="9119a-111">描述</span><span class="sxs-lookup"><span data-stu-id="9119a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="9119a-112">合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="9119a-112">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9119a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="9119a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9119a-114">項目</span><span class="sxs-lookup"><span data-stu-id="9119a-114">Element</span></span>|<span data-ttu-id="9119a-115">描述</span><span class="sxs-lookup"><span data-stu-id="9119a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="9119a-116">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="9119a-116">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9119a-117">您可以將標準群組為搜尋準則 (指定您要尋找的服務)，並且尋找終止準則 (搜尋應持續的時間長短)。</span><span class="sxs-lookup"><span data-stu-id="9119a-117">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9119a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9119a-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
