---
title: "訊息篩選條件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd5019668e865d2fea835b450d992d45b5273ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="message-filters"></a><span data-ttu-id="90e7d-102">訊息篩選條件</span><span class="sxs-lookup"><span data-stu-id="90e7d-102">Message Filters</span></span>
<span data-ttu-id="90e7d-103">為了實作內容架構路由，路由服務會使用 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作，該實作會檢查訊息的特定區段，例如位址、端點名稱或特定 XPath 陳述式。</span><span class="sxs-lookup"><span data-stu-id="90e7d-103">To implement content-based routing, the Routing Service uses <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that inspect specific sections of a message, such as the address, endpoint name, or a specific XPath statement.</span></span> <span data-ttu-id="90e7d-104">如果 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 提供的訊息篩選都不符合您的需要，您可以建立透過建立新的基底 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別實作來建立自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-104">If none of the message filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] meet your needs, you can create a custom filter by creating a new implementation of the base <xref:System.ServiceModel.Dispatcher.MessageFilter> class.</span></span>  
  
 <span data-ttu-id="90e7d-105">設定路由服務時，您必須定義篩選項目 (<xref:System.ServiceModel.Routing.Configuration.FilterElement>物件)，描述的型別**MessageFilter**和任何支援的資料，才能建立篩選器，例如要搜尋特定的字串值針對訊息內。</span><span class="sxs-lookup"><span data-stu-id="90e7d-105">When configuring the Routing Service, you must define filter elements (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objects) that describe the type of **MessageFilter** and any supporting data required to create the filter, such as specific string values to search for within the message.</span></span> <span data-ttu-id="90e7d-106">請注意，建立篩選項目只會定義個別訊息篩選，若要使用篩選評估和路由傳送訊息，您還必須定義篩選資料表 (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>)。</span><span class="sxs-lookup"><span data-stu-id="90e7d-106">Note that creating the filter elements only defines the individual message filters; to use the filters to evaluate and route messages you must also define a filter table (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).</span></span>  
  
 <span data-ttu-id="90e7d-107">篩選資料表中的每個項目都會參考篩選項目，並且指定將路由傳送訊息的目標用戶端端點 (如果訊息符合篩選的話)。</span><span class="sxs-lookup"><span data-stu-id="90e7d-107">Each entry in the filter table references a filter element and specifies the client endpoint that a message will be routed to if the message matches the filter.</span></span> <span data-ttu-id="90e7d-108">篩選資料表項目還可讓您指定備份端點的集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)，該集合會定義端點清單，當傳送至主要端點期間發生傳輸失敗事件時，會將訊息傳送至這些端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-108">The filter table entries also allow you to specify a collection of backup endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), which defines a list of endpoints that the message will be transmitted to in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="90e7d-109">這些端點會依指定的順序嘗試，直到其中一個成功為止。</span><span class="sxs-lookup"><span data-stu-id="90e7d-109">These endpoints will be tried in the order specified until one succeeds.</span></span>  
  
## <a name="message-filters"></a><span data-ttu-id="90e7d-110">訊息篩選條件</span><span class="sxs-lookup"><span data-stu-id="90e7d-110">Message Filters</span></span>  
 <span data-ttu-id="90e7d-111">路由服務使用的訊息篩選提供一般訊息選取功能，例如評估做為訊息傳送目標的端點名稱、SOAP 動作，或做為訊息傳送目標的位址或位址前置詞。</span><span class="sxs-lookup"><span data-stu-id="90e7d-111">The message filters used by the Routing Service provide common message selection functionality, such as evaluating the name of the endpoint that a message was sent to, the SOAP action, or the address or address prefix that the message was sent to.</span></span> <span data-ttu-id="90e7d-112">篩選也可以聯結 `AND` 條件，如此一來，只有在訊息同時符合兩個篩選時，才會路由傳送至端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-112">Filters can also be joined with an `AND` condition, so that messages will only be routed to an endpoint if the message matches both filters.</span></span> <span data-ttu-id="90e7d-113">您也可以透過建立自己的 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作來建立自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-113">You can also create custom filters by creating your own implementation of <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span></span>  
  
 <span data-ttu-id="90e7d-114">下表列出路由服務使用的 <xref:System.ServiceModel.Routing.Configuration.FilterType>、實作特定訊息篩選的類別，以及必要的 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> 參數。</span><span class="sxs-lookup"><span data-stu-id="90e7d-114">The following table lists the <xref:System.ServiceModel.Routing.Configuration.FilterType> used by the Routing Service, the class that implements the specific message filter, and the required <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parameters.</span></span>  
  
|<span data-ttu-id="90e7d-115">篩選條件類型</span><span class="sxs-lookup"><span data-stu-id="90e7d-115">Filter  Type</span></span>|<span data-ttu-id="90e7d-116">描述</span><span class="sxs-lookup"><span data-stu-id="90e7d-116">Description</span></span>|<span data-ttu-id="90e7d-117">篩選資料意義</span><span class="sxs-lookup"><span data-stu-id="90e7d-117">Filter Data Meaning</span></span>|<span data-ttu-id="90e7d-118">範例篩選</span><span class="sxs-lookup"><span data-stu-id="90e7d-118">Example Filter</span></span>|  
|------------------|-----------------|-------------------------|--------------------|  
|<span data-ttu-id="90e7d-119">動作</span><span class="sxs-lookup"><span data-stu-id="90e7d-119">Action</span></span>|<span data-ttu-id="90e7d-120">使用 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> 類別比對包含特定動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-120">Uses the <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> class to match messages containing a specific action.</span></span>|<span data-ttu-id="90e7d-121">要進行篩選的動作。</span><span class="sxs-lookup"><span data-stu-id="90e7d-121">The action to filter upon.</span></span>|<span data-ttu-id="90e7d-122">\<篩選器名稱 ="action1"filterType ="Action"filterData ="http://namespace/contract/operation"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-122">\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" /></span></span>|  
|<span data-ttu-id="90e7d-123">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="90e7d-123">EndpointAddress</span></span>|<span data-ttu-id="90e7d-124">使用<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>類別，與<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true`比對包含特定位址訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-124">Uses the <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address.</span></span>|<span data-ttu-id="90e7d-125">要篩選的位址 (在 [收件者] 標頭中)。</span><span class="sxs-lookup"><span data-stu-id="90e7d-125">The address to filter upon (in the To header).</span></span>|<span data-ttu-id="90e7d-126">\<篩選器名稱 ="address1"filterType ="EndpointAddress"filterData ="http://host/vdir/s.svc/b"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-126">\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  /></span></span>|  
|<span data-ttu-id="90e7d-127">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="90e7d-127">EndpointAddressPrefix</span></span>|<span data-ttu-id="90e7d-128">使用<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>類別，與<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true`比對包含特定位址前置詞的訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-128">Uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address prefix.</span></span>|<span data-ttu-id="90e7d-129">要使用最長的前置詞比對篩選的位址。</span><span class="sxs-lookup"><span data-stu-id="90e7d-129">The address to filter upon using longest prefix matching.</span></span>|<span data-ttu-id="90e7d-130">\<篩選器名稱 ="prefix1"filterType ="EndpointAddressPrefix"filterData ="http://host/"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-130">\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" /></span></span>|  
|<span data-ttu-id="90e7d-131">及</span><span class="sxs-lookup"><span data-stu-id="90e7d-131">And</span></span>|<span data-ttu-id="90e7d-132">使用固定在傳回之前評估兩項條件的 <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="90e7d-132">Uses the <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> class that always evaluates both conditions before returning.</span></span>|<span data-ttu-id="90e7d-133">不會使用 filterData;改為 filter1 和 filter2 具有的名稱，對應訊息篩選條件 （同樣在資料表中），它應該**AND**ed 放在一起。</span><span class="sxs-lookup"><span data-stu-id="90e7d-133">filterData is not used; instead filter1 and filter2 have the names of the corresponding message filters (also in the table), which should be **AND**ed together.</span></span>|<span data-ttu-id="90e7d-134">\<篩選器名稱 ="and1"filterType ="和"filter1 ="address1"filter2 ="action1"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-134">\<filter name="and1" filterType="And" filter1="address1" filter2="action1" /></span></span>|  
|<span data-ttu-id="90e7d-135">自訂</span><span class="sxs-lookup"><span data-stu-id="90e7d-135">Custom</span></span>|<span data-ttu-id="90e7d-136">使用者定義類型，該類型會延伸 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別並且擁有取用字串的建構函式。</span><span class="sxs-lookup"><span data-stu-id="90e7d-136">A user-defined type that extends the <xref:System.ServiceModel.Dispatcher.MessageFilter> class and has a constructor taking a string.</span></span>|<span data-ttu-id="90e7d-137">customType 屬性是要建立之類別的完整類型名稱；filterData 則是建立篩選時，要傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="90e7d-137">The customType attribute is the fully qualified type name of the class to create; filterData is the string to pass to the constructor when creating the filter.</span></span>|<span data-ttu-id="90e7d-138">\<篩選器名稱 ="custom1"filterType ="Custom"customType="CustomAssembly.CustomMsgFilter，CustomAssembly"filterData = 「 自訂資料 」 / ></span><span class="sxs-lookup"><span data-stu-id="90e7d-138">\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" /></span></span>|  
|<span data-ttu-id="90e7d-139">EndpointName</span><span class="sxs-lookup"><span data-stu-id="90e7d-139">EndpointName</span></span>|<span data-ttu-id="90e7d-140">使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> 類別，根據訊息到達的服務端點名稱比對訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-140">Uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> class to match messages based on the name of the service endpoint they arrived on.</span></span>|<span data-ttu-id="90e7d-141">服務端點的名稱，例如:"serviceEndpoint1"。</span><span class="sxs-lookup"><span data-stu-id="90e7d-141">The name of the service endpoint, for example: "serviceEndpoint1".</span></span>  <span data-ttu-id="90e7d-142">這應該是在路由服務上公開的其中一個端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-142">This should be one of the endpoints exposed on the Routing Service.</span></span>|<span data-ttu-id="90e7d-143">\<篩選器名稱 ="stock1"filterType = 「 端點 」 filterData ="SvcEndpoint"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-143">\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" /></span></span>|  
|<span data-ttu-id="90e7d-144">MatchAll</span><span class="sxs-lookup"><span data-stu-id="90e7d-144">MatchAll</span></span>|<span data-ttu-id="90e7d-145">使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="90e7d-145">Uses the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span> <span data-ttu-id="90e7d-146">此篩選會比對所有抵達的訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-146">This filter matches all arriving messages.</span></span>|<span data-ttu-id="90e7d-147">不會使用 filterData。</span><span class="sxs-lookup"><span data-stu-id="90e7d-147">filterData is not used.</span></span> <span data-ttu-id="90e7d-148">此篩選將固定比對所有訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-148">This filter will always match all messages.</span></span>|<span data-ttu-id="90e7d-149">\<篩選器名稱 ="matchAll1"filterType ="MatchAll"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-149">\<filter name="matchAll1" filterType="MatchAll" /></span></span>|  
|<span data-ttu-id="90e7d-150">XPath</span><span class="sxs-lookup"><span data-stu-id="90e7d-150">XPath</span></span>|<span data-ttu-id="90e7d-151">使用 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 類別比對訊息內的特定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="90e7d-151">Uses the <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> class to match specific XPath queries within the message.</span></span>|<span data-ttu-id="90e7d-152">比對訊息時使用的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="90e7d-152">The XPath query to use when matching messages.</span></span>|<span data-ttu-id="90e7d-153">\<篩選器名稱 ="XPath1"filterType ="XPath 」 filterData ="//ns:element"/ ></span><span class="sxs-lookup"><span data-stu-id="90e7d-153">\<filter name="XPath1" filterType="XPath" filterData="//ns:element" /></span></span>|  
  
 <span data-ttu-id="90e7d-154">下列範例會定義使用 XPath、EndpointName 和 PrefixEndpointAddress 訊息篩選的篩選項目。</span><span class="sxs-lookup"><span data-stu-id="90e7d-154">The following example defines filter entries that use the XPath, EndpointName, and PrefixEndpointAddress message filters.</span></span> <span data-ttu-id="90e7d-155">此範例也會示範針對 RoundRobinFilter1 和 RoundRobinFilter2 項目使用自訂篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-155">This example also demonstrates using a custom filter for the RoundRobinFilter1 and RoundRobinFilter2 entries.</span></span>  
  
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
>  <span data-ttu-id="90e7d-156">只定義篩選並不會針對該篩選評估訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-156">Simply defining a filter does not cause messages to be evaluated against the filter.</span></span> <span data-ttu-id="90e7d-157">篩選必須加入至篩選資料表，接著篩選資料表會與路由服務公開的服務端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="90e7d-157">The filter must be added to a filter table, which is then associated with the service endpoint exposed by the Routing Service.</span></span>  
  
### <a name="namespace-table"></a><span data-ttu-id="90e7d-158">命名空間資料表</span><span class="sxs-lookup"><span data-stu-id="90e7d-158">Namespace Table</span></span>  
 <span data-ttu-id="90e7d-159">使用 XPath 篩選時，包含 XPath 查詢的篩選資料可能因為使用命名空間而變得相當大。</span><span class="sxs-lookup"><span data-stu-id="90e7d-159">When using an XPath filter, the filter data that contains the XPath query can become extremely large due to the use of namespaces.</span></span> <span data-ttu-id="90e7d-160">為了減輕此問題所造成的影響，路由服務提供了一項功能，讓您使用命名空間資料表定義自己的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="90e7d-160">To alleviate this problem the Routing Service provides the ability to define your own namespace prefixes by using the namespace table.</span></span>  
  
 <span data-ttu-id="90e7d-161">命名空間資料表是 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> 物件的集合，該集合會定義可在 XPath 中使用之通用命名空間的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="90e7d-161">The namespace table is a collection of <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objects that defines the namespace prefixes for common namespaces that can be used in an XPath.</span></span> <span data-ttu-id="90e7d-162">以下為命名空間資料表中包含的預設命名空間和命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="90e7d-162">The following are the default namespaces and namespace prefixes that are contained in the namespace table.</span></span>  
  
|<span data-ttu-id="90e7d-163">前置詞</span><span class="sxs-lookup"><span data-stu-id="90e7d-163">Prefix</span></span>|<span data-ttu-id="90e7d-164">命名空間</span><span class="sxs-lookup"><span data-stu-id="90e7d-164">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="90e7d-165">s11</span><span class="sxs-lookup"><span data-stu-id="90e7d-165">s11</span></span>|<span data-ttu-id="90e7d-166">http://schemas.xmlsoap.org/soap/envelope</span><span class="sxs-lookup"><span data-stu-id="90e7d-166">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="90e7d-167">s12</span><span class="sxs-lookup"><span data-stu-id="90e7d-167">s12</span></span>|<span data-ttu-id="90e7d-168">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="90e7d-168">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="90e7d-169">wsaAugust2004</span><span class="sxs-lookup"><span data-stu-id="90e7d-169">wsaAugust2004</span></span>|<span data-ttu-id="90e7d-170">http://schemas.xmlsoap.org/ws/2004/08/addressing</span><span class="sxs-lookup"><span data-stu-id="90e7d-170">http://schemas.xmlsoap.org/ws/2004/08/addressing</span></span>|  
|<span data-ttu-id="90e7d-171">wsa10</span><span class="sxs-lookup"><span data-stu-id="90e7d-171">wsa10</span></span>|<span data-ttu-id="90e7d-172">http://www.w3.org/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="90e7d-172">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="90e7d-173">/sm</span><span class="sxs-lookup"><span data-stu-id="90e7d-173">sm</span></span>|<span data-ttu-id="90e7d-174">http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions</span><span class="sxs-lookup"><span data-stu-id="90e7d-174">http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions</span></span>|  
|<span data-ttu-id="90e7d-175">tempuri</span><span class="sxs-lookup"><span data-stu-id="90e7d-175">tempuri</span></span>|<span data-ttu-id="90e7d-176">http://tempuri.org</span><span class="sxs-lookup"><span data-stu-id="90e7d-176">http://tempuri.org</span></span>|  
|<span data-ttu-id="90e7d-177">ser</span><span class="sxs-lookup"><span data-stu-id="90e7d-177">ser</span></span>|<span data-ttu-id="90e7d-178">http://schemas.microsoft.com/2003/10/Serialization</span><span class="sxs-lookup"><span data-stu-id="90e7d-178">http://schemas.microsoft.com/2003/10/Serialization</span></span>|  
  
 <span data-ttu-id="90e7d-179">如果您事先知道將會在 XPath 查詢中使用特定命名空間，可以將它與唯一的命名空間前置詞一起加入至命名空間資料表，並且在任何 XPath 查詢中使用該前置詞，而不要使用完整的命名空間。</span><span class="sxs-lookup"><span data-stu-id="90e7d-179">When you know that you will be using a specific namespace in your XPath queries, you can add it to the namespace table along with a unique namespace prefix and use the prefix in any XPath query instead of the full namespace.</span></span> <span data-ttu-id="90e7d-180">下列範例會定義"custom""http://my.custom.namespace 」，接著在 filterData 包含的 XPath 查詢中使用的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="90e7d-180">The following example defines a prefix of "custom" for the namespace "http://my.custom.namespace", which is then used in the XPath query contained in filterData.</span></span>  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a><span data-ttu-id="90e7d-181">篩選資料表</span><span class="sxs-lookup"><span data-stu-id="90e7d-181">Filter Tables</span></span>  
 <span data-ttu-id="90e7d-182">雖然每一個篩選項目都會定義可套用至訊息的邏輯比較，但是篩選資料表仍然會提供篩選項目和目的用戶端端點之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="90e7d-182">While each filter element defines a logical comparison that can be applied to a message, the filter table provides the association between the filter element and the destination client endpoint.</span></span> <span data-ttu-id="90e7d-183">篩選資料表是具名的 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> 物件集合，會定義篩選、主要目的端點和替代備份端點清單之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="90e7d-183">A filter table is a named collection of <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objects that define the association between a filter, a primary destination endpoint, and a list of alternative backup endpoints.</span></span> <span data-ttu-id="90e7d-184">篩選資料表項目還可讓您針對每一項篩選條件指定選擇性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="90e7d-184">The filter table entries also allow you to specify an optional priority for each filter condition.</span></span> <span data-ttu-id="90e7d-185">下列範例會定義兩個篩選，然後定義篩選資料表，讓每個篩選與目的端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="90e7d-185">The following example defines two filters and then defines a filter table that associates each filter with a destination endpoint.</span></span>  
  
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
  
### <a name="filter-evaluation-priority"></a><span data-ttu-id="90e7d-186">篩選評估優先權</span><span class="sxs-lookup"><span data-stu-id="90e7d-186">Filter Evaluation Priority</span></span>  
 <span data-ttu-id="90e7d-187">根據預設，篩選資料表中的所有項目會同步評估，所評估的訊息會路由傳送至與每個相符篩選項目相關聯的端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-187">By default, all entries in the filter table are evaluated simultaneously, and the message being evaluated is routed to the endpoint(s) associated with each matching filter entry.</span></span> <span data-ttu-id="90e7d-188">如果有多個篩選評估為 `true`，而訊息為單向或雙工，則訊息會多點傳送至所有相符篩選的端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-188">If multiple filters evaluate to `true`, and the message is one-way or duplex, the message is multicast to the endpoints for all matching filters.</span></span> <span data-ttu-id="90e7d-189">但是要求-回覆訊息無法多點傳送，因為只能將一個回覆傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="90e7d-189">Request-reply messages cannot be multicast because only one reply can be returned to the client.</span></span>  
  
 <span data-ttu-id="90e7d-190">透過指定每個篩選的優先權層級，就可以實作更為複雜的路由邏輯，路由服務會先評估優先權層級最高的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-190">More complex routing logic can be implemented by specifying priority levels for each filter; the Routing Service evaluates all filters at the highest priority level first.</span></span> <span data-ttu-id="90e7d-191">如果訊息符合此層級的篩選，則不會處理較低優先權的篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-191">If a message matches a filter of this level, no filters of a lower priority are processed.</span></span> <span data-ttu-id="90e7d-192">例如，傳入的單向訊息會先針對優先權為 2 的所有篩選進行評估。</span><span class="sxs-lookup"><span data-stu-id="90e7d-192">For example, an incoming one-way message is first evaluated against all filters with a priority of 2.</span></span> <span data-ttu-id="90e7d-193">訊息不符合此優先權層級的任何篩選，因此接著會針對優先權 1 的篩選比較訊息。</span><span class="sxs-lookup"><span data-stu-id="90e7d-193">The message does not match any filter at this priority level, so next the message is compared against filters with a priority of 1.</span></span> <span data-ttu-id="90e7d-194">有兩個優先權 1 的篩選符合訊息，而因為這是單向訊息，因此會路由傳送至這兩個目的端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-194">Two priority 1 filters match the message, and because it is a one-way message it is routed to both destination endpoints.</span></span>  <span data-ttu-id="90e7d-195">由於在優先權 1 的篩選中找到相符項目，因此不會評估優先權 0 的篩選。</span><span class="sxs-lookup"><span data-stu-id="90e7d-195">Because a match was found among the priority 1 filters, no filters of priority 0 are evaluated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e7d-196">如果未指定任何篩選，則會使用預設優先權 0。</span><span class="sxs-lookup"><span data-stu-id="90e7d-196">If no priority is specified, the default priority of 0 is used.</span></span>  
  
 <span data-ttu-id="90e7d-197">下列範例會定義篩選資料表，針對資料表中參考的篩選指定優先權 2、1 和 0。</span><span class="sxs-lookup"><span data-stu-id="90e7d-197">The following example defines a filter table that specifies priorities of 2, 1, and 0 for the filters referenced in the table.</span></span>  
  
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
  
 <span data-ttu-id="90e7d-198">在前面的範例中，如果訊息符合 XPathFilter，則會路由傳送至 roundingCalcEndpoint，並且不會再評估資料表中的任何篩選，因為所有其他篩選都屬於較低的優先權。</span><span class="sxs-lookup"><span data-stu-id="90e7d-198">In the preceding example, if a message matches the XPathFilter, it will be routed to the roundingCalcEndpoint and no further filters in the table will be evaluated because all other filters are of a lower priority.</span></span> <span data-ttu-id="90e7d-199">不過，如果訊息不符合 XPathFilter，會接著針對下一個較低優先權的所有篩選 EndpointNameFilter 和 PrefixAddressFilter 進行評估。</span><span class="sxs-lookup"><span data-stu-id="90e7d-199">However, if the message does not match the XPathFilter it will then be evaluated against all filters of the next lower priority, EndpointNameFilter and PrefixAddressFilter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e7d-200">如果可行，請使用互斥的篩選，而不要指定優先權，因為優先權評估可能導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="90e7d-200">When possible, use exclusive filters instead of specifying a priority because priority evaluation can result in performance degradation.</span></span>  
  
### <a name="backup-lists"></a><span data-ttu-id="90e7d-201">備份清單</span><span class="sxs-lookup"><span data-stu-id="90e7d-201">Backup Lists</span></span>  
 <span data-ttu-id="90e7d-202">篩選資料表中的每一個篩選可以選擇性地指定備份清單，也就是具名的端點集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)。</span><span class="sxs-lookup"><span data-stu-id="90e7d-202">Each filter in the filter table can optionally specify a backup list, which is a named collection of endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>).</span></span> <span data-ttu-id="90e7d-203">此集合包含依順序排列的端點清單，訊息將在傳送至 <xref:System.ServiceModel.CommunicationException> 中指定的主要端點期間發生 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> 時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="90e7d-203">This collection contains an ordered list of endpoints that the message will be transmitted to in the event of a <xref:System.ServiceModel.CommunicationException> when sending to the primary endpoint specified in <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>.</span></span> <span data-ttu-id="90e7d-204">下列範例定義名為"backupServiceEndpoints"，其中包含兩個端點的備份清單。</span><span class="sxs-lookup"><span data-stu-id="90e7d-204">The following example defines a backup list named "backupServiceEndpoints" that contains two endpoints.</span></span>  
  
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
  
 <span data-ttu-id="90e7d-205">在上述範例中，如果傳送至主要端點"Destination"失敗，路由服務將嘗試傳送至每個端點中所列的順序，第一個傳送至 backupServiceQueue，如果接著傳送至 alternateServiceQueue傳送至 backupServiceQueue 失敗。</span><span class="sxs-lookup"><span data-stu-id="90e7d-205">In the preceding example, if a send to the primary endpoint "Destination" fails, the Routing Service will try sending to each endpoint in the sequence they are listed, first sending to backupServiceQueue and subsequently sending to alternateServiceQueue if the send to backupServiceQueue fails.</span></span> <span data-ttu-id="90e7d-206">如果所有備份端點都失敗，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="90e7d-206">If all backup endpoints fail, a fault is returned.</span></span>
