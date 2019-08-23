---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925588"
---
# <a name="findcriteria"></a><span data-ttu-id="3545a-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="3545a-101">\<findCriteria></span></span>
<span data-ttu-id="3545a-102">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="3545a-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="3545a-103">準則可以分組為搜尋準則 (指定您要尋找的服務), 並尋找終止準則 (搜尋應持續的時間長度)。</span><span class="sxs-lookup"><span data-stu-id="3545a-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="3545a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3545a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3545a-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3545a-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3545a-106">語法</span><span class="sxs-lookup"><span data-stu-id="3545a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3545a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3545a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3545a-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3545a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3545a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3545a-109">Attributes</span></span>  
  
|<span data-ttu-id="3545a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3545a-110">Attribute</span></span>|<span data-ttu-id="3545a-111">描述</span><span class="sxs-lookup"><span data-stu-id="3545a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3545a-112">持續期間</span><span class="sxs-lookup"><span data-stu-id="3545a-112">duration</span></span>|<span data-ttu-id="3545a-113">TimeSpan 值，用於指定等候網路服務回覆的時間上限。</span><span class="sxs-lookup"><span data-stu-id="3545a-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="3545a-114">預設持續時間為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="3545a-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="3545a-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="3545a-115">maxResults</span></span>|<span data-ttu-id="3545a-116">整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。</span><span class="sxs-lookup"><span data-stu-id="3545a-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="3545a-117">如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。</span><span class="sxs-lookup"><span data-stu-id="3545a-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="3545a-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="3545a-118">scopeMatchBy</span></span>|<span data-ttu-id="3545a-119">URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。</span><span class="sxs-lookup"><span data-stu-id="3545a-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="3545a-120">支援的範圍比對規則有五種。</span><span class="sxs-lookup"><span data-stu-id="3545a-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="3545a-121">如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。</span><span class="sxs-lookup"><span data-stu-id="3545a-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="3545a-122">如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="3545a-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3545a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="3545a-123">Child Elements</span></span>  
  
|<span data-ttu-id="3545a-124">項目</span><span class="sxs-lookup"><span data-stu-id="3545a-124">Element</span></span>|<span data-ttu-id="3545a-125">描述</span><span class="sxs-lookup"><span data-stu-id="3545a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3545a-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="3545a-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="3545a-127">Configuration 元素的集合, 其中包含工作流程服務合約類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3545a-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="3545a-128">\<尋找準則 > 的\<延伸模組 ></span><span class="sxs-lookup"><span data-stu-id="3545a-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="3545a-129">XML 項目物件的集合，這些物件會提供擴充。</span><span class="sxs-lookup"><span data-stu-id="3545a-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="3545a-130">\<scopes></span><span class="sxs-lookup"><span data-stu-id="3545a-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="3545a-131">物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="3545a-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="3545a-132">如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。</span><span class="sxs-lookup"><span data-stu-id="3545a-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3545a-133">父項目</span><span class="sxs-lookup"><span data-stu-id="3545a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3545a-134">項目</span><span class="sxs-lookup"><span data-stu-id="3545a-134">Element</span></span>|<span data-ttu-id="3545a-135">描述</span><span class="sxs-lookup"><span data-stu-id="3545a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3545a-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3545a-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="3545a-137">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="3545a-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3545a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3545a-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
