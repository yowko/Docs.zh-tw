---
title: 探索尋找與尋找準則
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: c95f8e1b48c4e58c6d521bd06df4a470999fa375
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095772"
---
# <a name="discovery-find-and-findcriteria"></a>探索尋找與尋找準則
探索尋找作業是由用戶端初始化，用於探索一項或多項服務，並且為探索中的其中一個主要動作。 執行尋找會透過網路傳送 WS-Discovery Probe 訊息。 符合指定準則的服務會以 WS-Discovery ProbeMatch 訊息回覆。 如需有關探索訊息的詳細資訊，請參閱[Ws-discovery 規格](https://go.microsoft.com/fwlink/?LinkID=122347)。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別會提供執行尋找作業的機制，並且讓執行探索用戶端的作業更為簡單。 它包含 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法，用於執行 (封鎖) 同步尋找，以及 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法，用於初始化非封鎖非同步尋找。 這兩種方法都採用 <xref:System.ServiceModel.Discovery.FindCriteria> 參數，並且透過 <xref:System.ServiceModel.Discovery.FindResponse> 物件將結果提供給使用者。  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> 有數個屬性，可以分組為搜尋準則，指定您要尋找哪些服務，以及尋找終止準則 （搜尋應持續多久）。 <xref:System.ServiceModel.Discovery.FindCriteria> 可以包含多個搜尋準則。 根據預設，服務必須符合所有元件，否則不會將本身視為相符的服務。 如果您要尋找僅符合部分準則的服務，可以在服務上實作自訂尋找邏輯，或是使用多個查詢。  
  
 搜尋準則包括：  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -選擇性。 要搜尋的服務合約名稱，以及搜尋服務時常用的準則。 如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。 請注意，在 WCF 端點僅支援一個合約。  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -選擇性。 範圍是絕對 URI，可用來分類個別服務端點。 在多個端點公開相同合約，而您希望能夠搜尋端點子集的情況下，可能會想要使用這種方式。 如果指定多個範圍，則只會回覆符合「所有」範圍的服務端點。  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -指定比對 Probe 訊息的端點中的範圍時所要使用的比對演算法。 支援的範圍比對規則有五種：  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> 基本的區分大小寫字串比較。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> 相符項目以區段分隔"/"。 搜尋 `http://contoso/building1` 符合與範圍的服務 `http://contoso/building/floor1`  。 請注意，它不符合 `http://contoso/building100` 因為最後兩個區段不相符。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> 比對範圍，以使用 LDAP URL 的區段。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> 比對完全使用 UUID 字串的範圍。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> 只有在未指定範圍的服務會比對。  
  
     如果未指定範圍比對規則，則會使用 <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix>。  
  
 終止準則包括：  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 若要在網路上等待服務回覆的-最大時間。 預設持續時間為 20 秒。  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 等候回覆-最大數目。 如果在 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 經過之前，先收到 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 回覆，尋找作業就會結束。  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> 具有<xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A>集合屬性，其中包含任何比對在網路上的服務傳送的回覆。 如果沒有任何服務回覆，則集合會是空的。 如果有一項或多項服務回覆，則每個回覆都會儲存在 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 物件中，其中包含與服務相關的位址、合約和一些額外資訊。  
  
 下列範例示範如何在程式碼中執行尋找作業。  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>另請參閱

- [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
- [探索範圍](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [基本](../../../../docs/framework/wcf/samples/basic-sample.md)
