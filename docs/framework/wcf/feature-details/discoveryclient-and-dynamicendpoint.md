---
title: "DiscoveryClient 與 DynamicEndpoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# DiscoveryClient 與 DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> 和 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 是用於用戶端的兩個類別，可搜尋服務。<xref:System.ServiceModel.Discovery.DiscoveryClient> 可提供您服務清單，用來比對一組特定準則，並讓您連接至服務。<xref:System.ServiceModel.Discovery.DynamicEndpoint> 可執行相同作業，而且可自動連接至找到的其中一項服務。任何端點都可成為 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，也可在組態中加入搜尋準則，因此當您的方案需要探索，但不要修改用戶端邏輯 \(僅需要修改端點\) 時，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 便非常有用。<xref:System.ServiceModel.Discovery.DiscoveryClient> 也可對搜尋作業進行更細微的控制。上述的用法和優點在下方有更詳盡的說明。  
  
## DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> 會定義同步和非同步的 Find 方法、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件。此外，它也可以定義同步和非同步的 Resolve 方法和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> 事件。您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 或 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法來搜尋服務。這些方法會使用 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體，可讓您指定合約型別名稱、範圍、要求的結果數目上限和範圍比對規則。呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法時，可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件。每當 <xref:System.ServiceModel.Discovery.DiscoveryClient> 收到來自服務的回應時，便會引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>。這可以用來顯示進度列，表示尋找作業的進度，也可以用於當收到尋找回應時要採取的動作。當尋找作業完成時，會引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件。發生的原因可能是已收到回應的數目上限，或已經過<xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>。當尋找作業完成時，會在 <xref:System.ServiceModel.Discovery.FindResponse> 執行個體中傳回結果。<xref:System.ServiceModel.Discovery.FindResponse> 包含一系列的 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>，其中含有位址、合約型別名稱、擴充、接聽 URI 和比對服務的範圍。您可以使用此資訊來連接並呼叫其中一個符合的服務。下列範例示範如何呼叫 [the M:System.ServiceModel.Discovery.DiscoveryClient.Find\(System.ServiceModel.Discovery.FindCriteria\)](assetId:///the M:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)?qualifyHint=False&autoUpgrade=True) 方法，以及使用傳回的中繼資料來呼叫找到的服務。使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 的好處是，您可快取找到的端點清單，並在稍後使用它們。您可以使用此快取建立自訂邏輯，以處理各種失敗狀況。  
  
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
   Console.WriteLine(“No matching endpoints found”);  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]進行非同步尋找呼叫的詳細資訊，請參閱[非同步尋找](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)。  
  
 您可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 和 <xref:System.ServiceModel.Discovery.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> 方法，找出以端點位址為基礎的服務。當端點位址不是網路位址時，這便非常有用。Resolve 方法會使用 <xref:System.ServiceModel.Discovery.ResolveCriteria> 執行個體，可讓您指定正在解析的服務端點位址、解析作業持續時間上限和組態集。下列範例示範如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 方法來解析服務。  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
  
```  
  
## DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 為標準端點 \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][標準端點](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)\)，可執行探索並自動選取符合的服務。只要建立 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，傳入要搜尋的合約和要使用的繫結，然後傳送 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 執行個體至 WCF 用戶端即可。下列範例示範如何建立和使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 來呼叫計算機服務。每次開啟用戶端時，都會執行探索。您也可以加入 `kind =”dynamicEndpoint”` 屬性至端點組態項目，將組態中定義的任何端點轉換為 <xref:System.ServiceModel.Discovery.DynamicEndpoint>。  
  
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
  
## 請參閱  
 [探索範圍](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)   
 [非同步尋找](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)   
 [基本](../../../../docs/framework/wcf/samples/basic-sample.md)