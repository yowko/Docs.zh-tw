---
title: 訊息篩選條件
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a0cc4663b9a3044d0ab80f03479a024acba50a3f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279775"
---
# <a name="message-filters"></a><span data-ttu-id="f8d7a-102">訊息篩選條件</span><span class="sxs-lookup"><span data-stu-id="f8d7a-102">Message Filters</span></span>

<span data-ttu-id="f8d7a-103">為了實作內容架構路由，路由服務會使用 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作，該實作會檢查訊息的特定區段，例如位址、端點名稱或特定 XPath 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-103">To implement content-based routing, the Routing Service uses <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that inspect specific sections of a message, such as the address, endpoint name, or a specific XPath statement.</span></span> <span data-ttu-id="f8d7a-104">如果 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 提供的訊息篩選都不符合您的需要，您可以建立透過建立新的基底 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別實作來建立自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-104">If none of the message filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] meet your needs, you can create a custom filter by creating a new implementation of the base <xref:System.ServiceModel.Dispatcher.MessageFilter> class.</span></span>  
  
 <span data-ttu-id="f8d7a-105">設定路由服務時，您必須 <xref:System.ServiceModel.Routing.Configuration.FilterElement>) 描述 **MessageFilter** 類型的物件，以及建立篩選器所需的任何支援資料（例如要在訊息內搜尋的特定字串值），來定義篩選元素 (物件。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-105">When configuring the Routing Service, you must define filter elements (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objects) that describe the type of **MessageFilter** and any supporting data required to create the filter, such as specific string values to search for within the message.</span></span> <span data-ttu-id="f8d7a-106">請注意，建立篩選項目只會定義個別訊息篩選，若要使用篩選評估和路由傳送訊息，您還必須定義篩選資料表 (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>)。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-106">Note that creating the filter elements only defines the individual message filters; to use the filters to evaluate and route messages you must also define a filter table (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).</span></span>  
  
 <span data-ttu-id="f8d7a-107">篩選資料表中的每個項目都會參考篩選項目，並且指定將路由傳送訊息的目標用戶端端點 (如果訊息符合篩選的話)。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-107">Each entry in the filter table references a filter element and specifies the client endpoint that a message will be routed to if the message matches the filter.</span></span> <span data-ttu-id="f8d7a-108">篩選資料表項目還可讓您指定備份端點的集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)，該集合會定義端點清單，當傳送至主要端點期間發生傳輸失敗事件時，會將訊息傳送至這些端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-108">The filter table entries also allow you to specify a collection of backup endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), which defines a list of endpoints that the message will be transmitted to in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="f8d7a-109">這些端點會依指定的順序嘗試，直到其中一個成功為止。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-109">These endpoints will be tried in the order specified until one succeeds.</span></span>  
  
## <a name="message-filters"></a><span data-ttu-id="f8d7a-110">訊息篩選條件</span><span class="sxs-lookup"><span data-stu-id="f8d7a-110">Message Filters</span></span>  

 <span data-ttu-id="f8d7a-111">路由服務使用的訊息篩選提供一般訊息選取功能，例如評估做為訊息傳送目標的端點名稱、SOAP 動作，或做為訊息傳送目標的位址或位址前置詞。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-111">The message filters used by the Routing Service provide common message selection functionality, such as evaluating the name of the endpoint that a message was sent to, the SOAP action, or the address or address prefix that the message was sent to.</span></span> <span data-ttu-id="f8d7a-112">篩選也可以聯結 `AND` 條件，如此一來，只有在訊息同時符合兩個篩選時，才會路由傳送至端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-112">Filters can also be joined with an `AND` condition, so that messages will only be routed to an endpoint if the message matches both filters.</span></span> <span data-ttu-id="f8d7a-113">您也可以透過建立自己的 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作來建立自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-113">You can also create custom filters by creating your own implementation of <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span></span>  
  
 <span data-ttu-id="f8d7a-114">下表列出路由服務使用的 <xref:System.ServiceModel.Routing.Configuration.FilterType>、實作特定訊息篩選的類別，以及必要的 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> 參數。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-114">The following table lists the <xref:System.ServiceModel.Routing.Configuration.FilterType> used by the Routing Service, the class that implements the specific message filter, and the required <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parameters.</span></span>  
  
|<span data-ttu-id="f8d7a-115">篩選條件類型</span><span class="sxs-lookup"><span data-stu-id="f8d7a-115">Filter  Type</span></span>|<span data-ttu-id="f8d7a-116">描述</span><span class="sxs-lookup"><span data-stu-id="f8d7a-116">Description</span></span>|<span data-ttu-id="f8d7a-117">篩選資料意義</span><span class="sxs-lookup"><span data-stu-id="f8d7a-117">Filter Data Meaning</span></span>|<span data-ttu-id="f8d7a-118">範例篩選</span><span class="sxs-lookup"><span data-stu-id="f8d7a-118">Example Filter</span></span>|  
|------------------|-----------------|-------------------------|--------------------|  
|<span data-ttu-id="f8d7a-119">動作</span><span class="sxs-lookup"><span data-stu-id="f8d7a-119">Action</span></span>|<span data-ttu-id="f8d7a-120">使用 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> 類別比對包含特定動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-120">Uses the <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> class to match messages containing a specific action.</span></span>|<span data-ttu-id="f8d7a-121">要進行篩選的動作。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-121">The action to filter upon.</span></span>|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|<span data-ttu-id="f8d7a-122">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="f8d7a-122">EndpointAddress</span></span>|<span data-ttu-id="f8d7a-123">使用 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> 類別， <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 搭配來比對包含特定位址的訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-123">Uses the <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address.</span></span>|<span data-ttu-id="f8d7a-124">要篩選的位址 (在 [收件者] 標頭中)。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-124">The address to filter upon (in the To header).</span></span>|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|<span data-ttu-id="f8d7a-125">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="f8d7a-125">EndpointAddressPrefix</span></span>|<span data-ttu-id="f8d7a-126">使用 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 類別， <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 搭配來比對包含特定位址首碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-126">Uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address prefix.</span></span>|<span data-ttu-id="f8d7a-127">要使用最長的前置詞比對篩選的位址。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-127">The address to filter upon using longest prefix matching.</span></span>|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|<span data-ttu-id="f8d7a-128">和</span><span class="sxs-lookup"><span data-stu-id="f8d7a-128">And</span></span>|<span data-ttu-id="f8d7a-129">使用固定在傳回之前評估兩項條件的 <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-129">Uses the <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> class that always evaluates both conditions before returning.</span></span>|<span data-ttu-id="f8d7a-130">未使用 filterData;相反地，filter1 和 filter2 具有對應之訊息篩選器的名稱 (也在資料表) 中，這應該 **與** ed 在一起。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-130">filterData is not used; instead filter1 and filter2 have the names of the corresponding message filters (also in the table), which should be **AND** ed together.</span></span>|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|<span data-ttu-id="f8d7a-131">自訂</span><span class="sxs-lookup"><span data-stu-id="f8d7a-131">Custom</span></span>|<span data-ttu-id="f8d7a-132">使用者定義類型，該類型會延伸 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別並且擁有取用字串的建構函式。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-132">A user-defined type that extends the <xref:System.ServiceModel.Dispatcher.MessageFilter> class and has a constructor taking a string.</span></span>|<span data-ttu-id="f8d7a-133">customType 屬性是要建立之類別的完整類型名稱；filterData 則是建立篩選時，要傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-133">The customType attribute is the fully qualified type name of the class to create; filterData is the string to pass to the constructor when creating the filter.</span></span>|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|<span data-ttu-id="f8d7a-134">EndpointName</span><span class="sxs-lookup"><span data-stu-id="f8d7a-134">EndpointName</span></span>|<span data-ttu-id="f8d7a-135">使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> 類別，根據訊息到達的服務端點名稱比對訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-135">Uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> class to match messages based on the name of the service endpoint they arrived on.</span></span>|<span data-ttu-id="f8d7a-136">服務端點的名稱，例如： "serviceEndpoint1"。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-136">The name of the service endpoint, for example: "serviceEndpoint1".</span></span>  <span data-ttu-id="f8d7a-137">這應該是在路由服務上公開的其中一個端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-137">This should be one of the endpoints exposed on the Routing Service.</span></span>|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|<span data-ttu-id="f8d7a-138">MatchAll</span><span class="sxs-lookup"><span data-stu-id="f8d7a-138">MatchAll</span></span>|<span data-ttu-id="f8d7a-139">使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-139">Uses the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span> <span data-ttu-id="f8d7a-140">此篩選會比對所有抵達的訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-140">This filter matches all arriving messages.</span></span>|<span data-ttu-id="f8d7a-141">不會使用 filterData。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-141">filterData is not used.</span></span> <span data-ttu-id="f8d7a-142">此篩選將固定比對所有訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-142">This filter will always match all messages.</span></span>|\<filter name="matchAll1" filterType="MatchAll" />|  
|<span data-ttu-id="f8d7a-143">XPath</span><span class="sxs-lookup"><span data-stu-id="f8d7a-143">XPath</span></span>|<span data-ttu-id="f8d7a-144">使用 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 類別比對訊息內的特定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-144">Uses the <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> class to match specific XPath queries within the message.</span></span>|<span data-ttu-id="f8d7a-145">比對訊息時使用的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-145">The XPath query to use when matching messages.</span></span>|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 <span data-ttu-id="f8d7a-146">下列範例會定義使用 XPath、EndpointName 和 PrefixEndpointAddress 訊息篩選的篩選項目。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-146">The following example defines filter entries that use the XPath, EndpointName, and PrefixEndpointAddress message filters.</span></span> <span data-ttu-id="f8d7a-147">此範例也會示範針對 RoundRobinFilter1 和 RoundRobinFilter2 項目使用自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-147">This example also demonstrates using a custom filter for the RoundRobinFilter1 and RoundRobinFilter2 entries.</span></span>  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> <span data-ttu-id="f8d7a-148">只定義篩選並不會針對該篩選評估訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-148">Simply defining a filter does not cause messages to be evaluated against the filter.</span></span> <span data-ttu-id="f8d7a-149">篩選必須加入至篩選資料表，接著篩選資料表會與路由服務公開的服務端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-149">The filter must be added to a filter table, which is then associated with the service endpoint exposed by the Routing Service.</span></span>  
  
### <a name="namespace-table"></a><span data-ttu-id="f8d7a-150">命名空間資料表</span><span class="sxs-lookup"><span data-stu-id="f8d7a-150">Namespace Table</span></span>  

 <span data-ttu-id="f8d7a-151">使用 XPath 篩選時，包含 XPath 查詢的篩選資料可能因為使用命名空間而變得相當大。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-151">When using an XPath filter, the filter data that contains the XPath query can become extremely large due to the use of namespaces.</span></span> <span data-ttu-id="f8d7a-152">為了減輕此問題所造成的影響，路由服務提供了一項功能，讓您使用命名空間資料表定義自己的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-152">To alleviate this problem the Routing Service provides the ability to define your own namespace prefixes by using the namespace table.</span></span>  
  
 <span data-ttu-id="f8d7a-153">命名空間資料表是 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> 物件的集合，該集合會定義可在 XPath 中使用之通用命名空間的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-153">The namespace table is a collection of <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objects that defines the namespace prefixes for common namespaces that can be used in an XPath.</span></span> <span data-ttu-id="f8d7a-154">以下為命名空間資料表中包含的預設命名空間和命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-154">The following are the default namespaces and namespace prefixes that are contained in the namespace table.</span></span>  
  
|<span data-ttu-id="f8d7a-155">前置詞</span><span class="sxs-lookup"><span data-stu-id="f8d7a-155">Prefix</span></span>|<span data-ttu-id="f8d7a-156">命名空間</span><span class="sxs-lookup"><span data-stu-id="f8d7a-156">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="f8d7a-157">s11</span><span class="sxs-lookup"><span data-stu-id="f8d7a-157">s11</span></span>|`http://schemas.xmlsoap.org/soap/envelope`|  
|<span data-ttu-id="f8d7a-158">s12</span><span class="sxs-lookup"><span data-stu-id="f8d7a-158">s12</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="f8d7a-159">wsaAugust2004</span><span class="sxs-lookup"><span data-stu-id="f8d7a-159">wsaAugust2004</span></span>|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|<span data-ttu-id="f8d7a-160">wsa10</span><span class="sxs-lookup"><span data-stu-id="f8d7a-160">wsa10</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="f8d7a-161">sm</span><span class="sxs-lookup"><span data-stu-id="f8d7a-161">sm</span></span>|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|<span data-ttu-id="f8d7a-162">tempuri</span><span class="sxs-lookup"><span data-stu-id="f8d7a-162">tempuri</span></span>|`http://tempuri.org`|  
|<span data-ttu-id="f8d7a-163">ser</span><span class="sxs-lookup"><span data-stu-id="f8d7a-163">ser</span></span>|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 <span data-ttu-id="f8d7a-164">如果您事先知道將會在 XPath 查詢中使用特定命名空間，可以將它與唯一的命名空間前置詞一起加入至命名空間資料表，並且在任何 XPath 查詢中使用該前置詞，而不要使用完整的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-164">When you know that you will be using a specific namespace in your XPath queries, you can add it to the namespace table along with a unique namespace prefix and use the prefix in any XPath query instead of the full namespace.</span></span> <span data-ttu-id="f8d7a-165">下列範例會定義命名空間的 "custom" 前置詞 `"http://my.custom.namespace"` ，然後在 filterData 所包含的 XPath 查詢中使用。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-165">The following example defines a prefix of "custom" for the namespace `"http://my.custom.namespace"`, which is then used in the XPath query contained in filterData.</span></span>  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a><span data-ttu-id="f8d7a-166">篩選資料表</span><span class="sxs-lookup"><span data-stu-id="f8d7a-166">Filter Tables</span></span>  

 <span data-ttu-id="f8d7a-167">雖然每一個篩選項目都會定義可套用至訊息的邏輯比較，但是篩選資料表仍然會提供篩選項目和目的用戶端端點之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-167">While each filter element defines a logical comparison that can be applied to a message, the filter table provides the association between the filter element and the destination client endpoint.</span></span> <span data-ttu-id="f8d7a-168">篩選資料表是具名的 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> 物件集合，會定義篩選、主要目的端點和替代備份端點清單之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-168">A filter table is a named collection of <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objects that define the association between a filter, a primary destination endpoint, and a list of alternative backup endpoints.</span></span> <span data-ttu-id="f8d7a-169">篩選資料表項目還可讓您針對每一項篩選條件指定選擇性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-169">The filter table entries also allow you to specify an optional priority for each filter condition.</span></span> <span data-ttu-id="f8d7a-170">下列範例會定義兩個篩選，然後定義篩選資料表，讓每個篩選與目的端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-170">The following example defines two filters and then defines a filter table that associates each filter with a destination endpoint.</span></span>  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a><span data-ttu-id="f8d7a-171">篩選評估優先權</span><span class="sxs-lookup"><span data-stu-id="f8d7a-171">Filter Evaluation Priority</span></span>  

 <span data-ttu-id="f8d7a-172">根據預設，篩選資料表中的所有項目會同步評估，所評估的訊息會路由傳送至與每個相符篩選項目相關聯的端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-172">By default, all entries in the filter table are evaluated simultaneously, and the message being evaluated is routed to the endpoint(s) associated with each matching filter entry.</span></span> <span data-ttu-id="f8d7a-173">如果有多個篩選評估為 `true`，而訊息為單向或雙工，則訊息會多點傳送至所有相符篩選的端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-173">If multiple filters evaluate to `true`, and the message is one-way or duplex, the message is multicast to the endpoints for all matching filters.</span></span> <span data-ttu-id="f8d7a-174">但是要求-回覆訊息無法多點傳送，因為只能將一個回覆傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-174">Request-reply messages cannot be multicast because only one reply can be returned to the client.</span></span>  
  
 <span data-ttu-id="f8d7a-175">透過指定每個篩選的優先權層級，就可以實作更為複雜的路由邏輯，路由服務會先評估優先權層級最高的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-175">More complex routing logic can be implemented by specifying priority levels for each filter; the Routing Service evaluates all filters at the highest priority level first.</span></span> <span data-ttu-id="f8d7a-176">如果訊息符合此層級的篩選，則不會處理較低優先權的篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-176">If a message matches a filter of this level, no filters of a lower priority are processed.</span></span> <span data-ttu-id="f8d7a-177">例如，傳入的單向訊息會先針對優先權為 2 的所有篩選進行評估。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-177">For example, an incoming one-way message is first evaluated against all filters with a priority of 2.</span></span> <span data-ttu-id="f8d7a-178">訊息不符合此優先權層級的任何篩選，因此接著會針對優先權 1 的篩選比較訊息。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-178">The message does not match any filter at this priority level, so next the message is compared against filters with a priority of 1.</span></span> <span data-ttu-id="f8d7a-179">有兩個優先權 1 的篩選符合訊息，而因為這是單向訊息，因此會路由傳送至這兩個目的端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-179">Two priority 1 filters match the message, and because it is a one-way message it is routed to both destination endpoints.</span></span>  <span data-ttu-id="f8d7a-180">由於在優先權 1 的篩選中找到相符項目，因此不會評估優先權 0 的篩選。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-180">Because a match was found among the priority 1 filters, no filters of priority 0 are evaluated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8d7a-181">如果未指定任何篩選，則會使用預設優先權 0。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-181">If no priority is specified, the default priority of 0 is used.</span></span>  
  
 <span data-ttu-id="f8d7a-182">下列範例會定義篩選資料表，針對資料表中參考的篩選指定優先權 2、1 和 0。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-182">The following example defines a filter table that specifies priorities of 2, 1, and 0 for the filters referenced in the table.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 <span data-ttu-id="f8d7a-183">在前面的範例中，如果訊息符合 XPathFilter，則會路由傳送至 roundingCalcEndpoint，並且不會再評估資料表中的任何篩選，因為所有其他篩選都屬於較低的優先權。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-183">In the preceding example, if a message matches the XPathFilter, it will be routed to the roundingCalcEndpoint and no further filters in the table will be evaluated because all other filters are of a lower priority.</span></span> <span data-ttu-id="f8d7a-184">不過，如果訊息不符合 XPathFilter，會接著針對下一個較低優先權的所有篩選 EndpointNameFilter 和 PrefixAddressFilter 進行評估。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-184">However, if the message does not match the XPathFilter it will then be evaluated against all filters of the next lower priority, EndpointNameFilter and PrefixAddressFilter.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8d7a-185">如果可行，請使用互斥的篩選，而不要指定優先權，因為優先權評估可能導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-185">When possible, use exclusive filters instead of specifying a priority because priority evaluation can result in performance degradation.</span></span>  
  
### <a name="backup-lists"></a><span data-ttu-id="f8d7a-186">備份清單</span><span class="sxs-lookup"><span data-stu-id="f8d7a-186">Backup Lists</span></span>  

 <span data-ttu-id="f8d7a-187">篩選資料表中的每一個篩選可以選擇性地指定備份清單，也就是具名的端點集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-187">Each filter in the filter table can optionally specify a backup list, which is a named collection of endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>).</span></span> <span data-ttu-id="f8d7a-188">此集合包含依順序排列的端點清單，訊息將在傳送至 <xref:System.ServiceModel.CommunicationException> 中指定的主要端點期間發生 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> 時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-188">This collection contains an ordered list of endpoints that the message will be transmitted to in the event of a <xref:System.ServiceModel.CommunicationException> when sending to the primary endpoint specified in <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>.</span></span> <span data-ttu-id="f8d7a-189">下列範例會定義名為 "backupServiceEndpoints" 的備份清單，其中包含兩個端點。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-189">The following example defines a backup list named "backupServiceEndpoints" that contains two endpoints.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 <span data-ttu-id="f8d7a-190">在上述範例中，如果傳送至主要端點 "Destination" 失敗，路由服務會嘗試以其列出的順序傳送至每個端點，先傳送至 backupServiceQueue，然後在傳送至 backupServiceQueue 失敗時傳送至 alternateServiceQueue。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-190">In the preceding example, if a send to the primary endpoint "Destination" fails, the Routing Service will try sending to each endpoint in the sequence they are listed, first sending to backupServiceQueue and subsequently sending to alternateServiceQueue if the send to backupServiceQueue fails.</span></span> <span data-ttu-id="f8d7a-191">如果所有備份端點都失敗，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8d7a-191">If all backup endpoints fail, a fault is returned.</span></span>
