---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855446"
---
# <a name="contracttypenames"></a><span data-ttu-id="39f0f-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="39f0f-101">\<contractTypeNames></span></span>
<span data-ttu-id="39f0f-102">組態區段，這個區段會指定合約型別名稱清單 (要搜尋之服務的合約名稱)，以及通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="39f0f-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="39f0f-103">如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。</span><span class="sxs-lookup"><span data-stu-id="39f0f-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="39f0f-104">請注意，在 Windows Communication Foundation （WCF）中，端點只能支援一個合約。</span><span class="sxs-lookup"><span data-stu-id="39f0f-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="39f0f-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39f0f-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="39f0f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="39f0f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="39f0f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="39f0f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="39f0f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="39f0f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<尋找準則 >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="39f0f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="39f0f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<contractTypeNames >**</span><span class="sxs-lookup"><span data-stu-id="39f0f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f0f-113">語法</span><span class="sxs-lookup"><span data-stu-id="39f0f-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f0f-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39f0f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="39f0f-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39f0f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f0f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="39f0f-116">Attributes</span></span>  
 <span data-ttu-id="39f0f-117">無。</span><span class="sxs-lookup"><span data-stu-id="39f0f-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39f0f-118">子元素</span><span class="sxs-lookup"><span data-stu-id="39f0f-118">Child Elements</span></span>  
  
|<span data-ttu-id="39f0f-119">項目</span><span class="sxs-lookup"><span data-stu-id="39f0f-119">Element</span></span>|<span data-ttu-id="39f0f-120">描述</span><span class="sxs-lookup"><span data-stu-id="39f0f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f0f-121">\<add></span><span class="sxs-lookup"><span data-stu-id="39f0f-121">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="39f0f-122">合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。</span><span class="sxs-lookup"><span data-stu-id="39f0f-122">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39f0f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="39f0f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="39f0f-124">項目</span><span class="sxs-lookup"><span data-stu-id="39f0f-124">Element</span></span>|<span data-ttu-id="39f0f-125">描述</span><span class="sxs-lookup"><span data-stu-id="39f0f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f0f-126">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="39f0f-126">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="39f0f-127">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="39f0f-127">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="39f0f-128">準則可以分組為搜尋準則（指定您要尋找的服務），並尋找終止準則（搜尋應持續的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="39f0f-128">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39f0f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39f0f-129">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
