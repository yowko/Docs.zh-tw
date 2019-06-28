---
title: 路由簡介
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 478c9aa6563cab4ba7769c56d7084c8716c43c58
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425373"
---
# <a name="routing-introduction"></a>路由簡介
路由服務提供了泛型的可外掛式 SOAP 媒介，此媒介能夠根據訊息內容路由傳送訊息。 透過路由服務，您就可以建立複雜路由邏輯，以便實作服務彙總、服務版本控制、優先權路由和多點傳送路由等案例。 路由服務還提供錯誤處理，可讓您設定備份端點清單，當傳送至主要目的端點期間發生錯誤時，訊息就會傳送至此清單中的端點。  
  
 這個主題的主要對象為路由服務的新手，內容涵蓋路由服務的基本組態和裝載。  
  
## <a name="configuration"></a>組態  
 路由服務會實作為 WCF 服務，公開一個或多個從用戶端接收訊息的服務端點，並且將訊息路由傳送至一個或多個目的端點。 服務提供了 <xref:System.ServiceModel.Routing.RoutingBehavior>，它會套用至服務所公開的服務端點。 這個行為可用來設定服務運作方式的各種不同方面。 為了方便使用組態檔進行設定，在指定的參數 **RoutingBehavior**。 在程式碼為基礎的情況下，這些參數會指定為一部分 <xref:System.ServiceModel.Routing.RoutingConfiguration> 物件，然後傳遞至 **RoutingBehavior**。  
  
 啟動時，這個行為會將 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> (用來執行訊息的 SOAP 處理) 加入至用戶端端點。 這可讓路由服務將訊息傳送至需要不同的端點**MessageVersion**比接收訊息所在的端點。 **RoutingBehavior**也會註冊一個服務延伸， <xref:System.ServiceModel.Routing.RoutingExtension> ，以修改路由服務組態，在執行階段提供了協助工具點。  
  
 **RoutingConfiguration**類別提供一致的方式設定和更新路由服務的組態。  它包含做為路由服務的設定，而用來設定參數**RoutingBehavior**當服務啟動時，或傳遞給**RoutingExtension**修改路由在執行階段組態。  
  
 路由邏輯可用來執行訊息的內容架構路由，它是透過將多個 <xref:System.ServiceModel.Dispatcher.MessageFilter> 物件群組為篩選資料表 (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 物件) 的方式定義。 內送訊息會根據包含在篩選資料表，並針對每個訊息篩選條件來評估**MessageFilter**符合訊息，並轉送至目的地端點。 使用指定的篩選資料表，應該用來將訊息路由傳送**RoutingBehavior**組態中，或透過使用程式碼**RoutingConfiguration**物件。  
  
### <a name="defining-endpoints"></a>定義端點  
 雖然您似乎應該藉由定義將要使用的路由邏輯開始進行設定，但實際上，您進行的第一個步驟應該是判斷要將訊息路由傳送至其中之端點的組織架構。 路由服務會使用合約定義用來接收和傳送訊息的通道組織結構，因此輸入通道的組織結構必須符合輸出通道的組織結構。  例如，如果您要路由傳送至使用要求-回覆通道組織結構的端點，則必須在傳入端點上使用相容的合約，例如 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。  
  
 這表示，如果您的目的端點使用擁有多種通訊模式 (例如混合單向和雙向作業) 的合約，您就無法建立單一服務端點來接收和路由傳送訊息至所有端點。 您必須判斷哪些端點擁有相容的組織結構，並且定義一個或多個服務端點，以便用來接收將路由傳送至目的端點的訊息。  
  
> [!NOTE]
> 使用指定多種通訊模式 (例如混合單向和雙向作業) 的合約時，其中一種解決方法，就是在路由服務中使用雙工合約，例如 <xref:System.ServiceModel.Routing.IDuplexSessionRouter>。 不過，這表示繫結必須具備雙工通訊的能力，但這並不適用於所有情況。 在不具備雙工能力的情況下，可能需要將通訊重構為多個端點或修改應用程式。  
  
 如需有關路由合約的詳細資訊，請參閱 [路由合約](routing-contracts.md)。  
  
 定義服務端點之後，您可以使用**RoutingBehavior**關聯特定**RoutingConfiguration**與端點。 使用組態檔設定路由服務時**RoutingBehavior**用來指定篩選資料表，其中包含用來處理此端點上收到的訊息的路由邏輯。 如果您要以程式設計方式設定路由服務可以使用指定的篩選資料表**RoutingConfiguration**。  
  
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
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
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
  
 這個範例會設定讓路由服務公開 （expose） 單一的端點位址為`http://localhost:8000/routingservice/router`，用來接收要路由傳送的訊息。 由於訊息會路由傳送至要求-回覆端點，因此服務端點會使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter> 合約。 此設定也會定義單一用戶端端點`http://localhost:8000/servicemodelsample/service`訊息會路由傳送至。 名為"routingTable1"篩選資料表 （未顯示） 包含用來路由訊息的路由邏輯，並使用是與服務端點相關聯**RoutingBehavior** （適用於組態檔） 或**RoutingConfiguration** （適用於以程式設計方式設定）。  
  
### <a name="routing-logic"></a>路由邏輯  
 若要定義用來路由傳送訊息的路由邏輯，您必須判斷傳入訊息內包含的哪些資訊可以單獨處理。 例如，如果要路由傳送的所有目的端點共用相同的 SOAP 動作，則訊息內所包含動作的值就不適合做為指標，且訊息不應該路由傳送至該值所指的特定端點。 如果您必須以唯一的方式將訊息路由傳送至某一個特定端點，則應該對唯一識別路由傳送訊息至其中之目的端點的資料進行篩選。  
  
 路由服務提供多種**MessageFilter**檢查訊息，例如位址、 動作、 端點名稱或甚至 XPath 查詢中的特定值的實作。 如果這些實作都不符合您的需求，您就可以建立自訂**MessageFilter**實作。 如需訊息篩選條件，並比較使用路由服務所實作的詳細資訊，請參閱[訊息篩選條件](message-filters.md)並[選擇篩選](choosing-a-filter.md)。  
  
 多個訊息篩選會組織成篩選資料表，將每個產生關聯**MessageFilter**與目的端點。 此外，篩選資料表還可以選擇性地用來指定備份端點清單，路由服務會在發生傳輸錯誤時，嘗試將訊息路由傳送至這些備份端點。  
  
 根據預設，篩選資料表內的所有訊息篩選都會同步評估，不過，您可以指定 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>，讓訊息篩選依照特定順序進行評估。 具有最高優先權的所有項目會先進行評估，而如果在較高優先權層級中找到相符項目，就不會對較低優先權的訊息篩選進行評估。 如需有關篩選資料表的詳細資訊，請參閱[訊息篩選條件](message-filters.md)。  
  
 下列範例使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，它會針對所有訊息評估為 `true`。 這**MessageFilter**新增至"routingTable1"篩選資料表，其會將**MessageFilter**與名為"CalculatorService"的用戶端端點。 **RoutingBehavior**然後指定 這個資料表應該用於處理服務端點的路由訊息。  
  
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
>  根據預設，路由服務只會評估訊息的標頭。 若要讓篩選存取訊息本文，您必須將 <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> 設定為 `false`。  
  
 **多點傳送**  
  
 雖然許多路由服務組態都使用僅將訊息路由傳送至一個特定端點的獨佔篩選邏輯，但您仍可能需要將特定訊息路由傳送至多個目的端點。 若要將訊息多點傳送至多個目的地，則下列條件必須為 true：  
  
- 通道組織結構不得為要求-回覆 (但可以是單向或雙工)，因為回應要求的用戶端應用程式只能接收一個回覆。  
  
- 評估訊息時，必須有多個篩選傳回 `true`。  
  
 如果這些條件都符合，則訊息會路由傳送至所有評估為 `true` 之篩選的所有端點。 下列範例會定義路由組態，如果訊息中的端點位址路由傳送至這兩個端點會導致 `http://localhost:8000/routingservice/router/rounding` 。  
  
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
  
### <a name="soap-processing"></a>SOAP 處理  
 若要支援不同的通訊協定之間的訊息路由**RoutingBehavior**根據預設會加入<xref:System.ServiceModel.Routing.SoapProcessingBehavior>訊息會路由傳送至的所有用戶端端點。 此行為會自動建立新**MessageVersion**之前的訊息路由傳送至端點，以及建立相容**MessageVersion**之前將它以傳回任何回應文件提出要求的用戶端應用程式。  
  
 若要建立新的所採取的步驟**MessageVersion**輸出訊息如下所示：  
  
 **要求處理**  
  
- 取得**MessageVersion**的輸出繫結/通道。  
  
- 取得原始訊息的本文讀取裝置。  
  
- 建立新的訊息使用相同的動作、 本文讀取裝置和新**MessageVersion**。  
  
- 如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>！ = **Addressing.None**，複製 To、 From、 FaultTo 和 RelatesTo 標頭，以新的訊息。  
  
- 將所有訊息屬性複製到新訊息。  
  
- 儲存處理回應時要使用的原始要求訊息。  
  
- 傳回新的要求訊息。  
  
 **回應處理**  
  
- 取得**MessageVersion**的原始要求訊息。  
  
- 取得已接收回應訊息的本文讀取裝置。  
  
- 建立新的回應訊息與相同的動作、 本文讀取裝置，而**MessageVersion**的原始要求訊息。  
  
- 如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>！ = **Addressing.None**，複製 To、 From、 FaultTo 和 RelatesTo 標頭，以新的訊息。  
  
- 將訊息屬性複製到新訊息。  
  
- 傳回新的回應訊息。  
  
 根據預設， **SoapProcessingBehavior**會自動新增至用戶端端點<xref:System.ServiceModel.Routing.RoutingBehavior>在服務啟動時; 不過，您可以控制是否 SOAP 處理加入至所有用戶端端點所使用<xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>屬性。 如果需要對 SOAP 處理進行更細微的控制，您也可以將此行為直接加入至特定端點，並且在端點層級啟用或停用此行為。  
  
> [!NOTE]
>  如果端點需要與原始要求訊息不同的 MessageVersion，且該端點的 SOAP 處理已停用，則您必須提供自訂機制來處理任何必要的 SOAP 修改，才能將訊息傳送至目的端點。  
  
 在下列範例中， **soapProcessingEnabled**屬性用來防止**SoapProcessingBehavior**自動新增至所有用戶端端點。  
  
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
  
### <a name="dynamic-configuration"></a>動態組態  
 當您加入其他用戶端端點，或是需要修改用來路由傳送訊息的篩選時，必須能夠在執行階段動態更新組態，以避免中斷目前正透過路由服務接收訊息的端點服務。 修改組態檔或主應用程式的程式碼不一定足夠，因為這兩種方法都需要回收應用程式，而這樣可能會導致目前正在傳輸的任何訊息遺失，且在等待服務重新啟動時可能發生停機。  
  
 您只能修改**RoutingConfiguration**以程式設計的方式。 雖然您一開始可以使用組態檔設定服務，您只能修改組態，在執行階段透過建構新**RoutingConfiguration**並將它傳遞做為參數<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A>方法由<xref:System.ServiceModel.Routing.RoutingExtension>服務延伸模組。 目前正在傳輸的任何訊息會繼續使用先前的設定，在呼叫之後收到的訊息時，路由傳送**ApplyConfiguration**使用新的組態。 下列範例示範建立路由服務的執行個體，然後修改組態。  
  
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
>  使用這個方式更新路由服務時，只能傳遞新組態， 而無法只修改目前組態的選取項目 (Element)，或是附加新項目 (Item) 至目前組態；您必須建立和傳遞取代現有組態的新組態。  
  
> [!NOTE]
>  使用舊組態開啟的任何工作階段都會繼續使用舊組態。 只有新的工作階段才會使用新組態。  
  
## <a name="error-handling"></a>錯誤處理  
 如果嘗試傳送訊息時發生任何 <xref:System.ServiceModel.CommunicationException>，則會進行錯誤處理。 這些例外狀況通常表示，嘗試與定義的用戶端端點 (如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>) 進行通訊時發生問題。 錯誤處理程式碼也會攔截並嘗試重新傳送的時機<xref:System.TimeoutException>發生時，這是另一個常見的例外狀況不衍生自**CommunicationException**。  
  
 發生上述其中一個例外狀況時，路由服務會容錯移轉至備份端點清單。 如果所有備份端點都發生通訊錯誤而失敗，或是某個端點傳回例外狀況，表示目的端服務內發生錯誤，則路由服務會將錯誤傳回至用戶端應用程式。  
  
> [!NOTE]
>  錯誤處理功能會擷取並處理嘗試傳送訊息和嘗試關閉通道時發生的例外狀況。 錯誤處理程式碼不是偵測或處理它與其進行通訊的應用程式端點所建立的例外狀況<xref:System.ServiceModel.FaultException>所擲回一項服務會出現在路由服務的身分**FaultMessage**並且送回用戶端。  
>   
>  如果路由服務嘗試回覆訊息時發生錯誤，您可能會在用戶端收到 <xref:System.ServiceModel.FaultException>，而非路由服務不存在時通常會收到的 <xref:System.ServiceModel.EndpointNotFoundException>。 路由服務可能會因而遮蓋例外狀況，而且除非您檢查巢狀例外狀況，否則無法提供完整透明度。  
  
### <a name="tracing-exceptions"></a>追蹤例外狀況  
 當傳送訊息至清單中的端點失敗，路由服務會追蹤產生的例外狀況資料，並附加為一個名為的訊息屬性的例外狀況詳細資料**例外狀況**。 如此可保留例外狀況資料，並且讓使用者透過訊息偵測器，以程式設計方式進行存取。  例外狀況資料是以一個訊息為單位儲存在字典中，該字典會將端點名稱對應至嘗試傳送訊息時發生的例外狀況詳細資料。  
  
### <a name="backup-endpoints"></a>備份端點  
 篩選資料表中的每一個篩選項目都可以選擇性地指定備份端點清單，這些端點會在傳送至主要端點發生傳輸錯誤時使用。 如果發生這類錯誤，路由服務會嘗試將訊息傳送至備份端點清單中的第一個項目。 如果此傳送嘗試同樣發生傳輸錯誤，則會嘗試備份清單中的下一個端點。 路由服務會繼續將訊息傳送至清單中的每一個端點，直到訊息接收成功、所有端點都傳回傳輸錯誤，或是端點傳回非傳輸錯誤為止。  
  
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
  
### <a name="supported-error-patterns"></a>支援的錯誤模式  
 下表說明與使用備份端點清單相容的模式，以及說明特定模式之錯誤處理詳細資料的附註。  
  
|模式|工作階段|Transaction|接收內容|支援的備份清單|注意|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|單向||||是|嘗試在備份端點上重新傳送訊息。 如果此訊息為多點傳送，則只有在失敗通道上的訊息會移到備份目的地。|  
|單向||✓||否|擲回例外狀況，且異動會復原。|  
|單向|||✓|是|嘗試在備份端點上重新傳送訊息。 成功接收訊息之後，完成所有接收內容。 如果任何端點未成功接收訊息，則不會完成接收內容。<br /><br /> 如果此訊息為多點傳送，則至少有一個端點 (主要或備份) 成功接收訊息才會完成接收內容。 如果任何多點傳送路徑中沒有任何端點成功接收訊息，則不會完成接收內容。|  
|單向||✓|✓|是|中止之前的交易、建立新交易，然後重新傳送所有訊息。 發生錯誤的訊息會傳送至備份目的地。<br /><br /> 建立其中所有傳輸都成功的異動之後，完成接收內容並認可異動。|  
|單向|✓|||是|嘗試在備份端點上重新傳送訊息。 在多點傳送的情況下，只有在發生錯誤之工作階段中的訊息，或是工作階段關閉失敗之工作階段中的訊息，才會重新傳送至備份目的地。|  
|單向|✓|✓||否|擲回例外狀況，且異動會復原。|  
|單向|✓||✓|是|嘗試在備份端點上重新傳送訊息。 所有訊息傳送完成且未發生錯誤之後，工作階段會指出沒有其他訊息，且路由服務成功關閉所有傳出工作階段通道，所有接收內容都已完成，以及傳入工作階段通道已關閉。|  
|單向|✓|✓|✓|是|中止目前的交易，並且建立新交易。 重新傳送工作階段中所有之前的訊息。 建立其中所有訊息已成功送出的異動，且工作階段指出沒有其他訊息之後，所有傳出工作階段通道都會關閉、異動的接收內容會全部完成、傳入工作階段通道會關閉，並且會認可異動。<br /><br /> 在多點傳送訊息的情況下，未發生錯誤的訊息會如以往重新傳送至相同的目的地，而發生錯誤的訊息則會傳送至備份目的地。|  
|雙向||||是|傳送至備份目的地。  通道傳回回應訊息之後，將回應傳回至原始用戶端。|  
|雙向|✓|||是|將通道上的所有訊息傳送至備份目的地。  通道傳回回應訊息之後，將回應傳回至原始用戶端。|  
|雙向||✓||否|擲回例外狀況，且異動會復原。|  
|雙向|✓|✓||否|擲回例外狀況，且異動會復原。|  
|雙工||||否|目前不支援非工作階段雙工通訊。|  
|雙工|✓|||是|傳送至備份目的地。|  
  
## <a name="hosting"></a>裝載  
 由於路由服務會當做 WCF 服務實作，因此必須在應用程式內自我裝載或是由 IIS 或 WAS 裝載。 建議您在 IIS、WAS 或 Windows 服務應用程式中裝載路由服務，以便利用這些裝載環境中提供的自動啟動和生命週期管理功能。  
  
 下列範例示範在應用程式中裝載路由服務。  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 若要在 IIS 或 WAS 內裝載路由服務，您必須建立服務檔案 (.svc) 或使用服務的組態架構啟動。 使用服務檔案時，必須使用 Service 參數指定 <xref:System.ServiceModel.Routing.RoutingService>。 下列範例包含範例服務檔案，可用來將路由服務裝載於 IIS 或 WAS。  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>路由服務與模擬  
 WCF 路由服務可以搭配模擬使用以傳送和接收訊息。 平常對模擬的所有 Windows 條件約束在這裡都適用。 當您撰寫您自己的服務時，如果需要設定服務或帳戶使用權限以使用模擬，就必須執行那些同樣的步驟來搭配路由服務使用模擬。 如需詳細資訊，請參閱 <<c0> [ 委派和模擬](delegation-and-impersonation-with-wcf.md)。  
  
 搭配路由服務的模擬需要使用 ASP.NET 模擬 (採用 ASP.NET 相容模式時) 或 Windows 認證 (這已設定為允許模擬)。 如需有關 ASP.NET 相容性模式的詳細資訊，請參閱[WCF 服務與 ASP.NET](wcf-services-and-aspnet.md)。  
  
> [!WARNING]
>  WCF 路由服務不支援基本驗證的模擬。  
  
 若要搭配路由服務使用 ASP.NET 模擬，請在服務裝載環境中啟用 ASP.NET 相容模式。 路由服務已經標記為允許 ASP.NET 相容模式，將會自動啟用模擬。 ASP.NET 與路由服務整合時，模擬是唯一受支援的使用方式。  
  
 若要搭配路由服務使用 Windows 認證模擬，您必須同時設定認證與服務。 用戶端認證物件 (<xref:System.ServiceModel.Security.WindowsClientCredential>，可從 <xref:System.ServiceModel.ChannelFactory> 中存取) 定義允許模擬所必須設定的 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性來存取。 最後，您必須在服務上設定 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 行為，才能將 `ImpersonateCallerForAllOperations` 設定為 `true`。 路由服務會使用這個旗標決定是否要建立用戶端，用來轉送已啟用模擬的訊息。  
  
## <a name="see-also"></a>另請參閱

- [訊息篩選](message-filters.md)
- [路由合約](routing-contracts.md)
- [選擇篩選](choosing-a-filter.md)
