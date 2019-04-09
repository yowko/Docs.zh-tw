---
title: DiscoveryClient 與 DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 1f3e9a25e82c4515ee649736ed162ab858aa6ff7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205026"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient 與 DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> 和<xref:System.ServiceModel.Discovery.DynamicEndpoint>是在用戶端用來搜尋服務的兩個類別。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 提供您一份符合特定的服務設定的準則，並可讓您連接到服務。 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 執行相同作業，此外，自動連接到其中一個找到的服務。 任何端點都可成為 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，也可在組態中加入搜尋準則，因此當您需要在方案中探索，但不想修改用戶端邏輯時 (您只需要修改端點)，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 便非常有用。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 另一方面可用來更細微的控制，對搜尋作業。 上述的用法和優點在下方有更詳盡的說明。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> 會定義同步和非同步的 Find 方法、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件。  此外，它也可以定義同步和非同步的 Resolve 方法和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> 事件。 您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 或 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法來搜尋服務。 這些方法會使用 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體，可讓您指定合約型別名稱、範圍、要求的結果數目上限和範圍比對規則。 呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 方法時，可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 事件。 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 每當引發<xref:System.ServiceModel.Discovery.DiscoveryClient>收到來自服務的回應。 這可以用來顯示進度列，表示尋找作業的進度， 也可以用於當收到尋找回應時要採取的動作。 當尋找作業完成時，會引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件。 發生的原因可能是已收到回應的數目上限，或已經過<xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>。 當尋找作業完成時，會在 <xref:System.ServiceModel.Discovery.FindResponse> 執行個體中傳回結果。 <xref:System.ServiceModel.Discovery.FindResponse> 包含一系列的 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>，其中含有位址、合約型別名稱、擴充、接聽 URI 和比對服務的範圍。 您可以使用此資訊來連接並呼叫其中一個符合的服務。 下列範例示範如何呼叫 System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) 方法，並使用傳回的中繼資料來呼叫找到的服務。 使用的優點<xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)>是您可以快取的端點，您發現，並在稍後使用它們的清單。 您可以使用此快取建立自訂邏輯，以處理各種失敗狀況。  
  
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
  
 下列範例示範如何以非同步方式執行尋找作業。  
  
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
  
 您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> 方法，找出以端點位址為基礎的服務。 當端點位址不是網路位址時，這便非常有用。 Resolve 方法會使用 <xref:System.ServiceModel.Discovery.ResolveCriteria> 執行個體，可讓您指定正在解析的服務端點位址、解析作業持續時間上限和組態集。 下列範例示範如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 方法來解析服務。  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 是標準的端點 (如需詳細資訊，請參閱 <<c0> [ 標準端點](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) 可執行探索，並會自動選取相符的服務。 只要建立 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，傳入要搜尋的合約和要使用的繫結，然後傳送 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 執行個體至 WCF 用戶端即可。 下列範例示範如何建立和使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 來呼叫計算機服務。 每次開啟用戶端時，都會執行探索。 也可以在組態中定義任何端點轉換成<xref:System.ServiceModel.Discovery.DynamicEndpoint>藉由新增`kind ="dynamicEndpoint"`屬性至端點的組態項目。  
  
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
  
## <a name="see-also"></a>另請參閱

- [探索範圍](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [基本](../../../../docs/framework/wcf/samples/basic-sample.md)
