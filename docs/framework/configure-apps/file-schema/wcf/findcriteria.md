---
title: '&lt;尋找準則&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 0a2fb7ae641f8ec34c518d8dc2c11fbc2ae26190
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146923"
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="fd3be-102">&lt;尋找準則&gt;</span><span class="sxs-lookup"><span data-stu-id="fd3be-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="fd3be-103">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="fd3be-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="fd3be-104">準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。</span><span class="sxs-lookup"><span data-stu-id="fd3be-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="fd3be-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd3be-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd3be-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fd3be-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3be-107">語法</span><span class="sxs-lookup"><span data-stu-id="fd3be-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd3be-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd3be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd3be-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fd3be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd3be-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fd3be-110">Attributes</span></span>  
  
|<span data-ttu-id="fd3be-111">屬性</span><span class="sxs-lookup"><span data-stu-id="fd3be-111">Attribute</span></span>|<span data-ttu-id="fd3be-112">描述</span><span class="sxs-lookup"><span data-stu-id="fd3be-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd3be-113">持續期間</span><span class="sxs-lookup"><span data-stu-id="fd3be-113">duration</span></span>|<span data-ttu-id="fd3be-114">TimeSpan 值，用於指定等候網路服務回覆的時間上限。</span><span class="sxs-lookup"><span data-stu-id="fd3be-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="fd3be-115">預設持續時間為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="fd3be-115">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="fd3be-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="fd3be-116">maxResults</span></span>|<span data-ttu-id="fd3be-117">整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。</span><span class="sxs-lookup"><span data-stu-id="fd3be-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="fd3be-118">如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。</span><span class="sxs-lookup"><span data-stu-id="fd3be-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="fd3be-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="fd3be-119">scopeMatchBy</span></span>|<span data-ttu-id="fd3be-120">URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。</span><span class="sxs-lookup"><span data-stu-id="fd3be-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="fd3be-121">支援的範圍比對規則有五種。</span><span class="sxs-lookup"><span data-stu-id="fd3be-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="fd3be-122">如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。</span><span class="sxs-lookup"><span data-stu-id="fd3be-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="fd3be-123">如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="fd3be-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd3be-124">子元素</span><span class="sxs-lookup"><span data-stu-id="fd3be-124">Child Elements</span></span>  
  
|<span data-ttu-id="fd3be-125">項目</span><span class="sxs-lookup"><span data-stu-id="fd3be-125">Element</span></span>|<span data-ttu-id="fd3be-126">描述</span><span class="sxs-lookup"><span data-stu-id="fd3be-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3be-127">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="fd3be-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="fd3be-128">包含工作流程服務合約型別的名稱的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="fd3be-128">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="fd3be-129">\<擴充功能 > 的\<尋找準則 ></span><span class="sxs-lookup"><span data-stu-id="fd3be-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="fd3be-130">XML 項目物件的集合，這些物件會提供擴充。</span><span class="sxs-lookup"><span data-stu-id="fd3be-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="fd3be-131">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="fd3be-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="fd3be-132">物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="fd3be-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="fd3be-133">如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。</span><span class="sxs-lookup"><span data-stu-id="fd3be-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd3be-134">父項目</span><span class="sxs-lookup"><span data-stu-id="fd3be-134">Parent Elements</span></span>  
  
|<span data-ttu-id="fd3be-135">項目</span><span class="sxs-lookup"><span data-stu-id="fd3be-135">Element</span></span>|<span data-ttu-id="fd3be-136">描述</span><span class="sxs-lookup"><span data-stu-id="fd3be-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3be-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fd3be-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fd3be-138">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="fd3be-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd3be-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd3be-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
