---
title: <add> 的 <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850541"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="84da6-102">\<新增 contractTypeNames > \<的 ></span><span class="sxs-lookup"><span data-stu-id="84da6-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="84da6-103">組態項目，這個項目會指定要搜尋之服務的合約名稱，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="84da6-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="84da6-104">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="84da6-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="84da6-105">請注意，在 Windows Communication Foundation （WCF）中，端點只能支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="84da6-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="84da6-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84da6-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84da6-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="84da6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="84da6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="84da6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="84da6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="84da6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<尋找準則 >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="84da6-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<contractTypeNames >** ](contracttypenames.md)</span><span class="sxs-lookup"><span data-stu-id="84da6-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)</span></span>\
<span data-ttu-id="84da6-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="84da6-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84da6-115">語法</span><span class="sxs-lookup"><span data-stu-id="84da6-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84da6-116">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84da6-116">Attributes and Elements</span></span>  
 <span data-ttu-id="84da6-117">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84da6-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84da6-118">屬性</span><span class="sxs-lookup"><span data-stu-id="84da6-118">Attributes</span></span>  
  
|<span data-ttu-id="84da6-119">屬性</span><span class="sxs-lookup"><span data-stu-id="84da6-119">Attribute</span></span>|<span data-ttu-id="84da6-120">說明</span><span class="sxs-lookup"><span data-stu-id="84da6-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84da6-121">NAME</span><span class="sxs-lookup"><span data-stu-id="84da6-121">name</span></span>|<span data-ttu-id="84da6-122">指定合約型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="84da6-122">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="84da6-123">namespace</span><span class="sxs-lookup"><span data-stu-id="84da6-123">namespace</span></span>|<span data-ttu-id="84da6-124">指定合約型別命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="84da6-124">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84da6-125">子元素</span><span class="sxs-lookup"><span data-stu-id="84da6-125">Child Elements</span></span>  
 <span data-ttu-id="84da6-126">None</span><span class="sxs-lookup"><span data-stu-id="84da6-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84da6-127">父項目</span><span class="sxs-lookup"><span data-stu-id="84da6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="84da6-128">項目</span><span class="sxs-lookup"><span data-stu-id="84da6-128">Element</span></span>|<span data-ttu-id="84da6-129">描述</span><span class="sxs-lookup"><span data-stu-id="84da6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84da6-130">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="84da6-130">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="84da6-131">合約型別名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="84da6-131">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84da6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84da6-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
