---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: ce2b1fdd85e0454f901bac393e2f44ae0c6da43f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178143"
---
# \<findCriteria>

<span data-ttu-id="19749-101">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="19749-101">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="19749-102">您可以將標準群組為搜尋準則 (指定您要尋找的服務)，並且尋找終止準則 (搜尋應持續的時間長短)。</span><span class="sxs-lookup"><span data-stu-id="19749-102">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="19749-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="19749-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19749-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19749-104">Attributes and Elements</span></span>  

 <span data-ttu-id="19749-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19749-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19749-106">屬性</span><span class="sxs-lookup"><span data-stu-id="19749-106">Attributes</span></span>  
  
|<span data-ttu-id="19749-107">屬性</span><span class="sxs-lookup"><span data-stu-id="19749-107">Attribute</span></span>|<span data-ttu-id="19749-108">描述</span><span class="sxs-lookup"><span data-stu-id="19749-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19749-109">duration</span><span class="sxs-lookup"><span data-stu-id="19749-109">duration</span></span>|<span data-ttu-id="19749-110">TimeSpan 值，用於指定等候網路服務回覆的時間上限。</span><span class="sxs-lookup"><span data-stu-id="19749-110">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="19749-111">預設持續時間為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="19749-111">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="19749-112">maxResults</span><span class="sxs-lookup"><span data-stu-id="19749-112">maxResults</span></span>|<span data-ttu-id="19749-113">整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。</span><span class="sxs-lookup"><span data-stu-id="19749-113">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="19749-114">如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。</span><span class="sxs-lookup"><span data-stu-id="19749-114">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="19749-115">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="19749-115">scopeMatchBy</span></span>|<span data-ttu-id="19749-116">URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。</span><span class="sxs-lookup"><span data-stu-id="19749-116">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="19749-117">支援的範圍比對規則有五種。</span><span class="sxs-lookup"><span data-stu-id="19749-117">There are five supported scope-matching rules.</span></span> <span data-ttu-id="19749-118">如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。</span><span class="sxs-lookup"><span data-stu-id="19749-118">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="19749-119">如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="19749-119">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19749-120">子元素</span><span class="sxs-lookup"><span data-stu-id="19749-120">Child Elements</span></span>  
  
|<span data-ttu-id="19749-121">項目</span><span class="sxs-lookup"><span data-stu-id="19749-121">Element</span></span>|<span data-ttu-id="19749-122">描述</span><span class="sxs-lookup"><span data-stu-id="19749-122">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="19749-123">設定元素的集合，其中包含工作流程服務合約類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="19749-123">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="19749-124">\<extensions> 的 \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="19749-124">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="19749-125">XML 項目物件的集合，這些物件會提供擴充。</span><span class="sxs-lookup"><span data-stu-id="19749-125">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="19749-126">物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="19749-126">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="19749-127">如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。</span><span class="sxs-lookup"><span data-stu-id="19749-127">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19749-128">父項目</span><span class="sxs-lookup"><span data-stu-id="19749-128">Parent Elements</span></span>  
  
|<span data-ttu-id="19749-129">項目</span><span class="sxs-lookup"><span data-stu-id="19749-129">Element</span></span>|<span data-ttu-id="19749-130">描述</span><span class="sxs-lookup"><span data-stu-id="19749-130">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="19749-131">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="19749-131">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19749-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19749-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
