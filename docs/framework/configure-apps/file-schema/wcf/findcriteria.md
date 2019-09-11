---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855162"
---
# <a name="findcriteria"></a><span data-ttu-id="3a97e-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="3a97e-101">\<findCriteria></span></span>
<span data-ttu-id="3a97e-102">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="3a97e-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="3a97e-103">準則可以分組為搜尋準則（指定您要尋找的服務），並尋找終止準則（搜尋應持續的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="3a97e-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
<span data-ttu-id="3a97e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a97e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a97e-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3a97e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3a97e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="3a97e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="3a97e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="3a97e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="3a97e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="3a97e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="3a97e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="3a97e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="3a97e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<尋找準則 >**</span><span class="sxs-lookup"><span data-stu-id="3a97e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a97e-111">語法</span><span class="sxs-lookup"><span data-stu-id="3a97e-111">Syntax</span></span>  
  
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
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a97e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a97e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3a97e-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3a97e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a97e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="3a97e-114">Attributes</span></span>  
  
|<span data-ttu-id="3a97e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="3a97e-115">Attribute</span></span>|<span data-ttu-id="3a97e-116">描述</span><span class="sxs-lookup"><span data-stu-id="3a97e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a97e-117">持續期間</span><span class="sxs-lookup"><span data-stu-id="3a97e-117">duration</span></span>|<span data-ttu-id="3a97e-118">TimeSpan 值，用於指定等候網路服務回覆的時間上限。</span><span class="sxs-lookup"><span data-stu-id="3a97e-118">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="3a97e-119">預設持續時間為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="3a97e-119">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="3a97e-120">maxResults</span><span class="sxs-lookup"><span data-stu-id="3a97e-120">maxResults</span></span>|<span data-ttu-id="3a97e-121">整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。</span><span class="sxs-lookup"><span data-stu-id="3a97e-121">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="3a97e-122">如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。</span><span class="sxs-lookup"><span data-stu-id="3a97e-122">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="3a97e-123">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="3a97e-123">scopeMatchBy</span></span>|<span data-ttu-id="3a97e-124">URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。</span><span class="sxs-lookup"><span data-stu-id="3a97e-124">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="3a97e-125">支援的範圍比對規則有五種。</span><span class="sxs-lookup"><span data-stu-id="3a97e-125">There are five supported scope-matching rules.</span></span> <span data-ttu-id="3a97e-126">如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。</span><span class="sxs-lookup"><span data-stu-id="3a97e-126">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="3a97e-127">如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="3a97e-127">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a97e-128">子元素</span><span class="sxs-lookup"><span data-stu-id="3a97e-128">Child Elements</span></span>  
  
|<span data-ttu-id="3a97e-129">項目</span><span class="sxs-lookup"><span data-stu-id="3a97e-129">Element</span></span>|<span data-ttu-id="3a97e-130">描述</span><span class="sxs-lookup"><span data-stu-id="3a97e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a97e-131">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="3a97e-131">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="3a97e-132">Configuration 元素的集合，其中包含工作流程服務合約類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a97e-132">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="3a97e-133">\<尋找準則 > 的\<延伸模組 ></span><span class="sxs-lookup"><span data-stu-id="3a97e-133">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="3a97e-134">XML 項目物件的集合，這些物件會提供擴充。</span><span class="sxs-lookup"><span data-stu-id="3a97e-134">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="3a97e-135">\<scopes></span><span class="sxs-lookup"><span data-stu-id="3a97e-135">\<scopes></span></span>](scopes.md)|<span data-ttu-id="3a97e-136">物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="3a97e-136">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="3a97e-137">如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。</span><span class="sxs-lookup"><span data-stu-id="3a97e-137">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a97e-138">父項目</span><span class="sxs-lookup"><span data-stu-id="3a97e-138">Parent Elements</span></span>  
  
|<span data-ttu-id="3a97e-139">項目</span><span class="sxs-lookup"><span data-stu-id="3a97e-139">Element</span></span>|<span data-ttu-id="3a97e-140">描述</span><span class="sxs-lookup"><span data-stu-id="3a97e-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a97e-141">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3a97e-141">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="3a97e-142">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="3a97e-142">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a97e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a97e-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
