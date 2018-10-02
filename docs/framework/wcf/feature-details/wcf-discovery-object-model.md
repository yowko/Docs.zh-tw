---
title: WCF 探索物件模型
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: b337eda40fc70a6d0e7b3aeccfc125e6e6bacf8f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046665"
---
# <a name="wcf-discovery-object-model"></a>WCF 探索物件模型
WCF 探索是由一組型別所組成，可提供統一的程式設計模型，讓您撰寫可在執行階段探索的服務，以及尋找和使用這些服務的用戶端。  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>建立可探索的服務和尋找服務  
 若要建立可探索的 WCF 服務，請將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機的 <xref:System.ServiceModel.Description.ServiceDescription> 並且加入探索端點。 如果服務設定為傳送公告訊息 (藉由加入 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>)，則會在服務主機開啟和關閉時傳送公告。  
  
 要接聽服務公告訊息的用戶端會裝載公告服務，並且加入一個或多個公告端點。 公告服務會接收公告訊息並引發公告事件。  
  
 用戶端會使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別搜尋可用的服務。 用戶端應用程式會具現化 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別，該類別會傳遞探索端點，指定要傳送探索訊息的目標。 用戶端會呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法，該方法會傳送 `Probe` 要求。 接聽探索訊息的服務會接收此 `Probe` 要求。 如果服務符合 `Probe` 中指定的準則，則會將 `ProbeMatch` 訊息傳回用戶端。  
  
## <a name="object-model"></a>物件模型  
 WCF 探索 API 會定義下列類別：  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
 
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> 類別會提供傳送公告訊息的同步和非同步方法。 公告訊息有兩種：Hello 和 Bye。 傳送 Hello 訊息表示服務可以使用，傳送 Bye 訊息則表示現有服務無法使用。 開發人員會建立 <xref:System.ServiceModel.Discovery.AnnouncementClient> 執行個體，傳遞 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 的執行個體做為建構函式參數。  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 表示具有固定公告合約的標準端點。 它是服務或用戶端用來傳送和接收公告訊息的類別。 根據預設，<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 類別會設定為使用 WS_Discovery 11 版的通訊協定。  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> 是系統提供的公告服務實作，會接收和處理公告訊息。 收到 Hello 或 Bye 訊息時，<xref:System.ServiceModel.Discovery.AnnouncementService> 執行個體會呼叫適當的虛擬方法 <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> 或 <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>，此方法會引發公告事件。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> 是用戶端應用程式用來尋找和解析可用服務的類別。 它提供同步和非同步方法，會分別依據指定的 <xref:System.ServiceModel.Discovery.FindCriteria> 和 <xref:System.ServiceModel.Discovery.ResolveCriteria> 尋找和解析服務。 開發人員會建立 <xref:System.ServiceModel.Discovery.DiscoveryClient> 執行個體並提供 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 的執行個體做為建構函式參數。  
  
 若要尋找服務，開發人員會叫用同步或 `Find` 方法，該方法會提供 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體，其中包含要使用的搜尋準則。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 會建立包含適當標頭的 `Probe` 訊息，並且傳送尋找要求。 由於隨時都可能會有多個未處理完畢的 `Find` 要求，因此用戶端會與接收的回應產生關聯，並且驗證回應。 接著用戶端會使用 `Find` 將結果傳遞至 <xref:System.ServiceModel.Discovery.FindResponse> 作業的呼叫端。  
  
 若要解析已知的服務，開發人員會叫用同步或非同步 `Resolve` 方法，該方法會提供包含已知服務之  <xref:System.ServiceModel.Discovery.ResolveCriteria> 的 <xref:System.ServiceModel.EndpointAddress> 執行個體。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 會建立包含適當標頭的 `Resolve` 訊息，並且傳送解析要求。 接收的回應會針對未處理完畢的解析要求產生關聯，結果則會使用 `Resolve` 傳遞至 <xref:System.ServiceModel.Discovery.ResolveResponse> 作業的呼叫端。  
  
 如果網路上有探索 Proxy 存在，且 <xref:System.ServiceModel.Discovery.DiscoveryClient> 是以多點傳送的方式傳送探索要求，則探索 Proxy 可能會在多點傳送隱藏 Hello 訊息的情況下回應。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 會在收到 Hello 訊息時引發 `ProxyAvailable` 事件，以回應未處理完畢的 `Find` 或 `Resolve` 要求。 `ProxyAvailable` 事件包含有關探索 Proxy 的 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>。 開發人員可自行決定是否使用這項資訊從特定模式切換成 Managed 模式。  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 表示具有固定探索合約的標準端點。 它是服務或用戶端用來傳送或接收探索訊息的類別。 根據預設，<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 會設定為使用 <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> 模式和 WSDiscovery11 WS-Discovery 版本。  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> 可在服務送出探索或共告訊息時，用來產生 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>。  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> 抽象類別會提供接收和處理 `Probe` 和 `Resolve` 訊息的架構。 當收到 `Probe` 訊息時，<xref:System.ServiceModel.Discovery.DiscoveryService> 會根據傳入的訊息建立 <xref:System.ServiceModel.Discovery.FindRequestContext> 的執行個體，並且叫用 <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> 虛擬方法。 當收到 `Resolve` 訊息時，<xref:System.ServiceModel.Discovery.DiscoveryService> 會叫用 <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> 虛擬方法。 您可以繼承自此類別，以提供自訂的探索服務實作。  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 抽象類別會提供接收和處理探索和公告訊息的架構。 當您實作自訂的探索 Proxy 時，可以繼承自此類別。 當透過多點傳送收到 `Probe` 訊息時，<xref:System.ServiceModel.Discovery.DiscoveryProxy> 類別會呼叫 `BeginShouldRedirectFind` 虛擬方法，判斷是否應該傳送多點傳送隱藏訊息。 如果開發人員決定不傳送多點傳送隱藏訊息，或是經由單點傳送收到 `Probe` 訊息，則會根據傳入的訊息建立 <xref:System.ServiceModel.Discovery.FindRequestContext> 類別的執行個體，並且叫用 `OnBeginFind` 虛擬方法。 當透過多點傳送收到 `Resolve` 訊息時，<xref:System.ServiceModel.Discovery.DiscoveryProxy> 類別會呼叫 `ShouldRedirectResolve` 虛擬方法，判斷是否應該傳送多點傳送隱藏訊息。 如果開發人員決定不傳送多點傳送隱藏訊息，或是經由單點傳送收到 `Resolve` 訊息，則會根據傳入的訊息建立 <xref:System.ServiceModel.Discovery.ResolveCriteria> 類別的執行個體，並且叫用 `OnBeginResolve` 虛擬方法。 當收到 Hello 或 Bye 訊息時，<xref:System.ServiceModel.Discovery.DiscoveryProxy> 會呼叫適當的虛擬方法 (`OnBeginOnlineAnnouncement` 或 `OnBeingOfflineAnnouncement`)，此方法會引發公告事件。  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> 類別表示要使用的探索通訊協定版本。  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 類別可用來控制端點的可搜尋性，指定延伸模組、其他合約型別名稱， 以及與端點相關聯的範圍。 此行為會加入至應用程式端點，以設定其 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>。 當 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機時，服務主機預設裝載的所有應用程式端點都會變成可探索。 開發人員可以將 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> 屬性設定為 `false`，藉此關閉特定端點的探索。  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 類別提供與服務發行之端點的版本無關的表示方式。 其中包含端點位址、接聽 URI、合約型別名稱、範圍、中繼資料版本，以及服務開發人員指定的延伸模組。 用戶端在 <xref:System.ServiceModel.Discovery.FindCriteria> 作業期間傳送的 `Probe` 會針對 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 進行比對。 如果準則相符，則 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 會傳回到用戶端。 <xref:System.ServiceModel.Discovery.ResolveCriteria> 中的端點位址會針對 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的端點位址進行比對。 如果準則相符，則 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 會傳回到用戶端。  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> 類別是與版本無關的類別，用來指定尋找服務時使用的準則。 該類別完全支援 WS-Discovery 所定義用於比對服務的準則。 此外還包含延伸模組，可讓開發人員用來指定自訂值，這些值可以在比對過程中使用。 開發人員可以指定 `Find` (此方式會指定開發人員尋找的服務總數)，或是指定 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> (這個值會指定用戶端等待回應的時間長度)，藉此提供 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 作業的終止準則。  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> 類別是透過探索服務具現化，該服務根據用戶端初始化 `Probe` 作業時收到的 `Find` 訊息而定。 其中包含用戶端指定的 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體。  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> 類別會傳回到 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 的呼叫端，並且包含 `Find` 作業的回應。 此外也會出現在 <xref:System.ServiceModel.Discovery.FindCompletedEventArgs> 中。 它包含 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合，也就是已探索端點和 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 和 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> 字典的集合。  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> 類別是與版本無關的類別，用來指定解析已知服務時使用的準則。 它包含已知服務的端點位址。 開發人員可以透過指定 <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A> (它會指定用戶端等待回應的時間長度) 的方式，提供解析作業的終止準則。  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> 會傳回到 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 方法的呼叫端，並且包含 `Resolve` 作業的回應。 此外也會出現在 <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs> 中。 它包含 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的執行個體，也就是已探索的端點和 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> 的執行個體。  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 類別可讓開發人員將探索功能加入至服務。 您可將此行為加入至 <xref:System.ServiceModel.ServiceHost>。 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 類別會反覆查看加入至服務主機的應用程式端點，並且從可探索端點建立 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合。 根據預設，所有端點都可以探索。 藉由將 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 加入至特定端點，即可控制該特定端點的探索能力。 如果將公告端點加入至 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>，則所有可探索端點的公告都會在服務主機開啟或關閉時，透過各個公告端點傳送。  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 類別是標準公告端點，也就是針對透過 UDP 多點傳送繫結的公告預先設定的端點。 根據預設，<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 會設定為使用 WSApril2005 WS_Discovery 版本。  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 類別是標準探索端點，會針對透過 UDP 多點傳送繫結的探索預先設定。 根據預設，<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 會設定為使用 WSDiscovery11 WS-Discovery 版本和 <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> 模式。
