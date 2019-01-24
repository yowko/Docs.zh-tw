---
title: DiscoveryClient 與 DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6e7b1cf13309ba6fc1da424649c667efe255278e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709984"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="48d60-102">DiscoveryClient 與 DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="48d60-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="48d60-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> 和 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 是用於用戶端的兩個類別，可搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="48d60-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> 可提供您服務清單，用來比對一組特定準則，並讓您連接至服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="48d60-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 可執行相同作業，而且可自動連接至找到的其中一項服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="48d60-106">任何端點都可成為 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，也可在組態中加入搜尋準則，因此當您需要在方案中探索，但不想修改用戶端邏輯時 (您只需要修改端點)，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 便非常有用。</span><span class="sxs-lookup"><span data-stu-id="48d60-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="48d60-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> 也可對搜尋作業進行更細微的控制。</span><span class="sxs-lookup"><span data-stu-id="48d60-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="48d60-108">上述的用法和優點在下方有更詳盡的說明。</span><span class="sxs-lookup"><span data-stu-id="48d60-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="48d60-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="48d60-109">DiscoveryClient</span></span>  
 <span data-ttu-id="48d60-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> 會定義同步和非同步的 Find 方法、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="48d60-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="48d60-111">此外，它也可以定義同步和非同步的 Resolve 方法和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="48d60-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="48d60-112">您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 或 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法來搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="48d60-113">這些方法會使用 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體，可讓您指定合約型別名稱、範圍、要求的結果數目上限和範圍比對規則。</span><span class="sxs-lookup"><span data-stu-id="48d60-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="48d60-114">呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 方法時，可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 事件。</span><span class="sxs-lookup"><span data-stu-id="48d60-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="48d60-115">每當 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 收到來自服務的回應時，便會引發 <xref:System.ServiceModel.Discovery.DiscoveryClient>。</span><span class="sxs-lookup"><span data-stu-id="48d60-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="48d60-116">這可以用來顯示進度列，表示尋找作業的進度，</span><span class="sxs-lookup"><span data-stu-id="48d60-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="48d60-117">也可以用於當收到尋找回應時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="48d60-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="48d60-118">當尋找作業完成時，會引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="48d60-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="48d60-119">發生的原因可能是已收到回應的數目上限，或已經過<xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>。</span><span class="sxs-lookup"><span data-stu-id="48d60-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="48d60-120">當尋找作業完成時，會在 <xref:System.ServiceModel.Discovery.FindResponse> 執行個體中傳回結果。</span><span class="sxs-lookup"><span data-stu-id="48d60-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="48d60-121"><xref:System.ServiceModel.Discovery.FindResponse> 包含一系列的 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>，其中含有位址、合約型別名稱、擴充、接聽 URI 和比對服務的範圍。</span><span class="sxs-lookup"><span data-stu-id="48d60-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="48d60-122">您可以使用此資訊來連接並呼叫其中一個符合的服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="48d60-123">下列範例示範如何呼叫 System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) 方法，並使用傳回的中繼資料來呼叫找到的服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="48d60-124">使用的優點<xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)>是您可以快取的端點，您發現，並在稍後使用它們的清單。</span><span class="sxs-lookup"><span data-stu-id="48d60-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="48d60-125">您可以使用此快取建立自訂邏輯，以處理各種失敗狀況。</span><span class="sxs-lookup"><span data-stu-id="48d60-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="48d60-126">下列範例示範如何以非同步方式執行尋找作業。</span><span class="sxs-lookup"><span data-stu-id="48d60-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="48d60-127">您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> 方法，找出以端點位址為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="48d60-128">當端點位址不是網路位址時，這便非常有用。</span><span class="sxs-lookup"><span data-stu-id="48d60-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="48d60-129">Resolve 方法會使用 <xref:System.ServiceModel.Discovery.ResolveCriteria> 執行個體，可讓您指定正在解析的服務端點位址、解析作業持續時間上限和組態集。</span><span class="sxs-lookup"><span data-stu-id="48d60-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="48d60-130">下列範例示範如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 方法來解析服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="48d60-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="48d60-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="48d60-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 是標準的端點 (如需詳細資訊，請參閱 <<c0> [ 標準端點](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) 可執行探索，並會自動選取相符的服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="48d60-133">只要建立 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，傳入要搜尋的合約和要使用的繫結，然後傳送 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 執行個體至 WCF 用戶端即可。</span><span class="sxs-lookup"><span data-stu-id="48d60-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="48d60-134">下列範例示範如何建立和使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 來呼叫計算機服務。</span><span class="sxs-lookup"><span data-stu-id="48d60-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="48d60-135">每次開啟用戶端時，都會執行探索。</span><span class="sxs-lookup"><span data-stu-id="48d60-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="48d60-136">也可以在組態中定義任何端點轉換成<xref:System.ServiceModel.Discovery.DynamicEndpoint>藉由新增`kind ="dynamicEndpoint"`屬性至端點的組態項目。</span><span class="sxs-lookup"><span data-stu-id="48d60-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="48d60-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48d60-137">See also</span></span>
- [<span data-ttu-id="48d60-138">探索範圍</span><span class="sxs-lookup"><span data-stu-id="48d60-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="48d60-139">基本</span><span class="sxs-lookup"><span data-stu-id="48d60-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
