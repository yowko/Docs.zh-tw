---
title: "路由簡介 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# 路由簡介
路由服務提供了泛型的可外掛式 SOAP 媒介，此媒介能夠根據訊息內容路由傳送訊息。  透過路由服務，您就可以建立複雜路由邏輯，以便實作服務彙總、服務版本控制、優先權路由和多點傳送路由等案例。  路由服務還提供錯誤處理，可讓您設定備份端點清單，當傳送至主要目的端點期間發生錯誤時，訊息就會傳送至此清單中的端點。  
  
 這個主題的主要對象為路由服務的新手，內容涵蓋路由服務的基本組態和裝載。  
  
## 組態  
 路由服務會實作為 WCF 服務，公開一個或多個從用戶端接收訊息的服務端點，並且將訊息路由傳送至一個或多個目的端點。  服務提供了 <xref:System.ServiceModel.Routing.RoutingBehavior>，它會套用至服務所公開的服務端點。  這個行為可用來設定服務運作方式的各種不同方面。  為了方便使用組態檔進行設定，參數會在 **RoutingBehavior** 上指定。  在程式碼架構案例中，這些參數會指定為 <xref:System.ServiceModel.Routing.RoutingConfiguration> 物件的一部分，而該物件接著可以傳遞至 **RoutingBehavior**。  
  
 啟動時，這個行為會將 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> \(用來執行訊息的 SOAP 處理\) 加入至用戶端端點。  如此可讓路由服務將訊息傳送至需要與接收訊息所在端點所需不同 **MessageVersion** 的端點。  **RoutingBehavior** 還會註冊服務延伸 <xref:System.ServiceModel.Routing.RoutingExtension>，該延伸提供了協助工具點，可在執行階段修改路由服務組態。  
  
 **RoutingConfiguration** 類別提供設定和更新路由服務組態的一致方式。  它包含做為路由服務設定的參數，並且會在服務啟動時用來設定 **RoutingBehavior**，或是傳遞至 **RoutingExtension** 以便在執行階段修改路由組態。  
  
 路由邏輯可用來執行訊息的內容架構路由，它是透過將多個 <xref:System.ServiceModel.Dispatcher.MessageFilter> 物件群組為篩選資料表 \(<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 物件\) 的方式定義。  傳入訊息會針對篩選資料表中包含的訊息篩選進行評估，並且針對每一個符合訊息的 **MessageFilter** 轉送至目的端點。  應該用來路由傳送訊息的篩選資料表，是使用組態中的 **RoutingBehavior** 或是使用 **RoutingConfiguration** 物件透過程式碼指定。  
  
### 定義端點  
 雖然您似乎應該藉由定義將要使用的路由邏輯開始進行設定，但實際上，您進行的第一個步驟應該是判斷要將訊息路由傳送至其中之端點的組織架構。  路由服務會使用合約定義用來接收和傳送訊息的通道組織結構，因此輸入通道的組織結構必須符合輸出通道的組織結構。  例如，如果您要路由傳送至使用要求\-回覆通道組織結構的端點，則必須在傳入端點上使用相容的合約，例如 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。  
  
 這表示，如果您的目的端點使用擁有多種通訊模式 \(例如混合單向和雙向作業\) 的合約，您就無法建立單一服務端點來接收和路由傳送訊息至所有端點。  您必須判斷哪些端點擁有相容的組織結構，並且定義一個或多個服務端點，以便用來接收將路由傳送至目的端點的訊息。  
  
> [!NOTE]
>  使用指定多種通訊模式 \(例如混合單向和雙向作業\) 的合約時，其中一種解決方法，就是在路由服務中使用雙工合約，例如 <xref:System.ServiceModel.Routing.IDuplexSessionRouter>。  不過，這表示繫結必須具備雙工通訊的能力，但這並不適用於所有情況。  在不具備雙工能力的情況下，可能需要將通訊重構為多個端點或修改應用程式。  
  
 如需路由合約的詳細資訊，請參閱[路由合約](../../../../docs/framework/wcf/feature-details/routing-contracts.md)。  
  
 定義服務端點之後，您就可以使用 **RoutingBehavior** 讓特定 **RoutingConfiguration** 與端點產生關聯。  使用組態檔設定路由服務時，會使用 **RoutingBehavior** 指定包含路由邏輯的篩選資料表，該邏輯會用來處理此端點上收到的訊息。  如果您要以程式設計方式設定路由服務，可以使用 **RoutingConfiguration** 指定篩選資料表。  
  
 下列範例會同時以程式設計方式和使用組態檔的方式，定義路由服務使用的服務和用戶端端點。  
  
```xml  
<services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 這個範例會設定讓路由服務公開位址為 “http:\/\/localhost:8000\/routingservice\/router” 單一端點，該端點會用來接收要路由傳送的訊息。  由於訊息會路由傳送至要求\-回覆端點，因此服務端點會使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter> 合約。  這個組態也會定義單一用戶端端點 “http:\/\/localhost:8000\/servicemodelsample\/service”，訊息會路由傳送至該端點。  名為 “routingTable1” 的篩選資料表 \(未顯示\) 會包含用來路由傳送訊息的路由邏輯，並且使用 **RoutingBehavior** \(適用組態檔\) 或 **RoutingConfiguration** \(適用程式化組態\) 與服務端點產生關聯。  
  
### 路由邏輯  
 若要定義用來路由傳送訊息的路由邏輯，您必須判斷傳入訊息內包含的哪些資訊可以單獨處理。  例如，如果要路由傳送的所有目的端點共用相同的 SOAP 動作，則訊息內所包含動作的值就不適合做為指標，且訊息不應該路由傳送至該值所指的特定端點。  如果您必須以唯一的方式將訊息路由傳送至某一個特定端點，則應該對唯一識別路由傳送訊息至其中之目的端點的資料進行篩選。  
  
 路由服務提供數項 **MessageFilter** 實作，這些實作會檢查訊息內特定的值，例如位址、動作、端點名稱，甚至 XPath 查詢。  如果這些實作都不符合需要，您可以建立自訂 **MessageFilter** 實作。  如需訊息篩選和路由服務所使用實作之比較的詳細資訊，請參閱[訊息篩選條件](../../../../docs/framework/wcf/feature-details/message-filters.md)和[選擇篩選](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)。  
  
 多個訊息篩選會組織成篩選資料表，這些資料表會將每個 **MessageFilter** 與目的端點產生關聯。  此外，篩選資料表還可以選擇性地用來指定備份端點清單，路由服務會在發生傳輸錯誤時，嘗試將訊息路由傳送至這些備份端點。  
  
 根據預設，篩選資料表內的所有訊息篩選都會同步評估，不過，您可以指定 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>，讓訊息篩選依照特定順序進行評估。  具有最高優先權的所有項目會先進行評估，而如果在較高優先權層級中找到相符項目，就不會對較低優先權的訊息篩選進行評估。  如需篩選資料表的詳細資訊，請參閱[訊息篩選條件](../../../../docs/framework/wcf/feature-details/message-filters.md)。  
  
 下列範例使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，它會針對所有訊息評估為 `true`。  這個 **MessageFilter** 會加入至 “routingTable1” 篩選資料表，該資料表會將 **MessageFilter** 與名為 “CalculatorService” 的用戶端端點產生關聯。  接著，**RoutingBehavior** 會指定此資料表應該用來路由傳送服務端點所處理的訊息。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  根據預設，路由服務只會評估訊息的標頭。  若要讓篩選存取訊息本文，您必須將 <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> 設定為 `false`。  
  
 **多點傳送**  
  
 雖然許多路由服務組態都使用僅將訊息路由傳送至一個特定端點的獨佔篩選邏輯，但您仍可能需要將特定訊息路由傳送至多個目的端點。  若要將訊息多點傳送至多個目的地，則下列條件必須為 true：  
  
-   通道組織結構不得為要求\-回覆 \(但可以是單向或雙工\)，因為回應要求的用戶端應用程式只能接收一個回覆。  
  
-   評估訊息時，必須有多個篩選傳回 `true`。  
  
 如果這些條件都符合，則訊息會路由傳送至所有評估為 `true` 之篩選的所有端點。  下列範例會定義路由組態，如果訊息中的端點位址為 http:\/\/localhost:8000\/routingservice\/router\/rounding，則會將訊息同時路由傳送至兩個端點。  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### SOAP 處理  
 為了在不同通訊協定之間支援訊息路由，**RoutingBehavior** 預設會將 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> 加入至訊息會路由傳送至其中的所有用戶端端點。  這個行為會在訊息路由傳送至端點之前自動建立新的 **MessageVersion**，以及在任何回應文件傳回至要求的用戶端應用程式之前，為其建立相容的 **MessageVersion**。  
  
 針對傳出訊息建立新 **MessageVersion** 的步驟如下：  
  
 **要求處理**  
  
-   取得傳出繫結\/通道的 **MessageVersion**。  
  
-   取得原始訊息的本文讀取裝置。  
  
-   建立擁有相同動作、本文讀取裝置和新 **MessageVersion** 的新訊息。  
  
-   如果 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> \!\= **Addressing.None**，則將 To、From、FaultTo 和 RelatesTo 標頭複製到新訊息。  
  
-   將所有訊息屬性複製到新訊息。  
  
-   儲存處理回應時要使用的原始要求訊息。  
  
-   傳回新的要求訊息。  
  
 **回應處理**  
  
-   取得原始要求訊息的 **MessageVersion**。  
  
-   取得已接收回應訊息的本文讀取裝置。  
  
-   建立擁有相同動作、本文讀取裝置和原始要求訊息之 **MessageVersion** 的新回應訊息。  
  
-   如果 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> \!\= **Addressing.None**，則將 To、From、FaultTo 和 RelatesTo 標頭複製到新訊息。  
  
-   將訊息屬性複製到新訊息。  
  
-   傳回新的回應訊息。  
  
 根據預設，<xref:System.ServiceModel.Routing.RoutingBehavior> 會在服務啟動時，自動將 **SoapProcessingBehavior** 加入至用戶端端點，不過，您可以使用 <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> 屬性控制是否將 SOAP 處理加入至所有用戶端端點。  如果需要對 SOAP 處理進行更細微的控制，您也可以將此行為直接加入至特定端點，並且在端點層級啟用或停用此行為。  
  
> [!NOTE]
>  如果端點需要與原始要求訊息不同的 MessageVersion，且該端點的 SOAP 處理已停用，則您必須提供自訂機制來處理任何必要的 SOAP 修改，才能將訊息傳送至目的端點。  
  
 在下列範例中，**soapProcessingEnabled** 屬性可避免將 **SoapProcessingBehavior** 自動加入至所有用戶端端點。  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### 動態組態  
 當您加入其他用戶端端點，或是需要修改用來路由傳送訊息的篩選時，必須能夠在執行階段動態更新組態，以避免中斷目前正透過路由服務接收訊息的端點服務。  修改組態檔或主應用程式的程式碼不一定足夠，因為這兩種方法都需要回收應用程式，而這樣可能會導致目前正在傳輸的任何訊息遺失，且在等待服務重新啟動時可能發生停機。  
  
 您只能以程式設計方式修改 **RoutingConfiguration**。  雖然您一開始可以使用組態檔設定服務，但是在執行階段，您只能透過建構新的 **RoutingConfigution** 並且將它當做參數傳遞至 <xref:System.ServiceModel.Routing.RoutingExtension> 服務延伸所公開的 <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> 方法來修改組態。  目前正在傳輸的任何訊息都會繼續使用舊組態路由傳送，而在呼叫 **ApplyConfiguration** 之後收到的訊息則會使用新組態。  下列範例示範建立路由服務的執行個體，然後修改組態。  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  使用這個方式更新路由服務時，只能傳遞新組態，  而無法只修改目前組態的選取項目 \(Element\)，或是附加新項目 \(Item\) 至目前組態；您必須建立和傳遞取代現有組態的新組態。  
  
> [!NOTE]
>  使用舊組態開啟的任何工作階段都會繼續使用舊組態。  只有新的工作階段才會使用新組態。  
  
## 錯誤處理  
 如果嘗試傳送訊息時發生任何 <xref:System.ServiceModel.CommunicationException>，則會進行錯誤處理。  這些例外狀況通常表示，嘗試與定義的用戶端端點 \(如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>\) 進行通訊時發生問題。  錯誤處理程式碼也會在 <xref:System.TimeoutException> 發生時攔截並嘗試重新傳送，這是另一個常見的例外狀況，它不是衍生自 **CommunicationException**。  
  
 發生上述其中一個例外狀況時，路由服務會容錯移轉至備份端點清單。  如果所有備份端點都發生通訊錯誤而失敗，或是某個端點傳回例外狀況，表示目的端服務內發生錯誤，則路由服務會將錯誤傳回至用戶端應用程式。  
  
> [!NOTE]
>  錯誤處理功能會擷取並處理嘗試傳送訊息和嘗試關閉通道時發生的例外狀況。  錯誤處理程式碼的主要目的不是偵測或處理與其進行通訊的應用程式端點所建立的例外狀況。服務擲回的 <xref:System.ServiceModel.FaultException> 會在路由服務中顯示為 **FaultMessage**，並且送回用戶端。  
>   
>  如果路由服務嘗試回覆訊息時發生錯誤，您可能會在用戶端收到 <xref:System.ServiceModel.FaultException>，而非路由服務不存在時通常會收到的 <xref:System.ServiceModel.EndpointNotFoundException>。  路由服務可能會因而遮蓋例外狀況，而且除非您檢查巢狀例外狀況，否則無法提供完整透明度。  
  
### 追蹤例外狀況  
 將訊息傳送至清單中的端點失敗時，路由服務會追蹤產生的例外狀況資料，並且將例外狀況詳細資料附加為名為 **Exceptions** 的訊息屬性。  如此可保留例外狀況資料，並且讓使用者透過訊息偵測器，以程式設計方式進行存取。  例外狀況資料是以一個訊息為單位儲存在字典中，該字典會將端點名稱對應至嘗試傳送訊息時發生的例外狀況詳細資料。  
  
### 備份端點  
 篩選資料表中的每一個篩選項目都可以選擇性地指定備份端點清單，這些端點會在傳送至主要端點發生傳輸錯誤時使用。  如果發生這類錯誤，路由服務會嘗試將訊息傳送至備份端點清單中的第一個項目。  如果此傳送嘗試同樣發生傳輸錯誤，則會嘗試備份清單中的下一個端點。  路由服務會繼續將訊息傳送至清單中的每一個端點，直到訊息接收成功、所有端點都傳回傳輸錯誤，或是端點傳回非傳輸錯誤為止。  
  
 下列範例設定讓路由服務使用備份清單。  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### 支援的錯誤模式  
 下表說明與使用備份端點清單相容的模式，以及說明特定模式之錯誤處理詳細資料的附註。  
  
|模式|工作階段|異動|接收內容|支援的備份清單|備註|  
|--------|----------|--------|----------|-------------|--------|  
|單向||||是|嘗試在備份端點上重新傳送訊息。  如果此訊息為多點傳送，則只有在失敗通道上的訊息會移到備份目的地。|  
|單向||![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||否|擲回例外狀況，且交易會復原。|  
|單向|||![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|是|嘗試在備份端點上重新傳送訊息。  成功接收訊息之後，完成所有接收內容。  如果任何端點未成功接收訊息，則不會完成接收內容。<br /><br /> 如果此訊息為多點傳送，則至少有一個端點 \(主要或備份\) 成功接收訊息才會完成接收內容。  如果任何多點傳送路徑中沒有任何端點成功接收訊息，則不會完成接收內容。|  
|單向||![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|是|中止之前的交易、建立新交易，然後重新傳送所有訊息。  發生錯誤的訊息會傳送至備份目的地。<br /><br /> 建立其中所有傳輸都成功的交易之後，完成接收內容並認可交易。|  
|單向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||是|嘗試在備份端點上重新傳送訊息。  在多點傳送的情況下，只有在發生錯誤之工作階段中的訊息，或是工作階段關閉失敗之工作階段中的訊息，才會重新傳送至備份目的地。|  
|單向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||否|擲回例外狀況，且交易會復原。|  
|單向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|是|嘗試在備份端點上重新傳送訊息。  所有訊息傳送完成且未發生錯誤之後，工作階段會指出沒有其他訊息，且路由服務成功關閉所有傳出工作階段通道，所有接收內容都已完成，以及傳入工作階段通道已關閉。|  
|單向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|是|中止目前的交易，並且建立新交易。  重新傳送工作階段中所有之前的訊息。  建立其中所有訊息已成功送出的交易，且工作階段指出沒有其他訊息之後，所有傳出工作階段通道都會關閉、交易的接收內容會全部完成、傳入工作階段通道會關閉，並且會認可交易。<br /><br /> 在多點傳送訊息的情況下，未發生錯誤的訊息會如以往重新傳送至相同的目的地，而發生錯誤的訊息則會傳送至備份目的地。|  
|雙向||||是|傳送至備份目的地。  通道傳回回應訊息之後，將回應傳回至原始用戶端。|  
|雙向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||是|將通道上的所有訊息傳送至備份目的地。  通道傳回回應訊息之後，將回應傳回至原始用戶端。|  
|雙向||![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||否|擲回例外狀況，且交易會復原。|  
|雙向|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||否|擲回例外狀況，且交易會復原。|  
|雙工||||否|目前不支援非工作階段雙工通訊。|  
|雙工|![核取標記](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||是|傳送至備份目的地。|  
  
## 裝載  
 由於路由服務會當做 WCF 服務實作，因此必須在應用程式內自我裝載或是由 IIS 或 WAS 裝載。  建議您在 IIS、WAS 或 Windows 服務應用程式中裝載路由服務，以便利用這些裝載環境中提供的自動啟動和生命週期管理功能。  
  
 下列範例示範在應用程式中裝載路由服務。  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
  
```  
  
 若要在 IIS 或 WAS 內裝載路由服務，您必須建立服務檔案 \(.svc\) 或使用服務的組態架構啟動。  使用服務檔案時，必須使用 Service 參數指定 <xref:System.ServiceModel.Routing.RoutingService>。  下列範例包含範例服務檔案，可用來將路由服務裝載於 IIS 或 WAS。  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
  
```  
  
## 路由服務與模擬  
 WCF 路由服務可以搭配模擬使用以傳送和接收訊息。  平常對模擬的所有 Windows 條件約束在這裡都適用。  當您撰寫您自己的服務時，如果需要設定服務或帳戶使用權限以使用模擬，就必須執行那些同樣的步驟來搭配路由服務使用模擬。  如需詳細資訊，請參閱[委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。  
  
 搭配路由服務的模擬需要使用 ASP.NET 模擬 \(採用 ASP.NET 相容模式時\) 或 Windows 認證 \(這已設定為允許模擬\)。  如需 ASP.NET 相容模式的詳細資訊，請參閱 [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。  
  
> [!WARNING]
>  WCF 路由服務不支援基本驗證的模擬。  
  
 若要搭配路由服務使用 ASP.NET 模擬，請在服務裝載環境中啟用 ASP.NET 相容模式。  路由服務已經標記為允許 ASP.NET 相容模式，將會自動啟用模擬。  ASP.NET 與路由服務整合時，模擬是唯一受支援的使用方式。  
  
 若要搭配路由服務使用 Windows 認證模擬，您必須同時設定認證與服務。  用戶端認證物件 \(<xref:System.ServiceModel.Security.WindowsClientCredential>，可從 <xref:System.ServiceModel.ChannelFactory> 中存取\) 定義允許模擬所必須設定的 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性來存取。  最後，您必須在服務上設定 <xref:System.ServiceModel.Description.ServiceAuthorization> 行為，才能將 `ImpersonateCallerForAllOperations` 設定為 `true`。  路由服務會使用這個旗標決定是否要建立用戶端，用來轉送已啟用模擬的訊息。  
  
## 請參閱  
 [訊息篩選條件](../../../../docs/framework/wcf/feature-details/message-filters.md)   
 [路由合約](../../../../docs/framework/wcf/feature-details/routing-contracts.md)   
 [選擇篩選](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)