---
title: HOW TO：使用篩選
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 2c8c5519d31d1d57c1c568599964b97043f806a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496340"
---
# <a name="how-to-use-filters"></a>HOW TO：使用篩選
本主題概要說明建立使用多個篩選條件之路由組態所需的基本步驟。 在此範例中，會將訊息路由至計算機服務的兩種實作 (regularCalc 與 roundingCalc)。 兩項實作都支援相同的作業，不過其中一個服務會在傳回之前將所有的計算結果四捨五入至最接近的整數值。 用戶端應用程式必須能夠指出是否要使用四捨五入後的服務版本，如果未指定任何服務偏好設定，則會在兩項服務之間平衡訊息負載。 由這兩項服務公開的作業為：  
  
-   Add  
  
-   Subtract  
  
-   乘法  
  
-   Divide  
  
 由於兩項服務皆實作同一個作業，因此您不能使用 [動作] 篩選條件，因為訊息中指定的動作不會是唯一的動作。 相反的，您必須進行額外的工作，以確保訊息能夠路由至正確的端點。  
  
### <a name="determine-unique-data"></a>若要判斷唯一資料  
  
1.  因為這兩項服務實作會處理相同的作業，而且它們與不是由其傳回的資料完全相同，所以包含在來自用戶端應用程式之訊息中的基底資料的唯一性質不足，無法藉此判斷路由要求方式。 但是，如果用戶端應用程式在訊息中加入唯一的標頭值，您就可以利用這個值來判斷訊息的路由方式。  
  
     在這個範例中，如果用戶端應用程式需要由四捨五入計算機來處理訊息，就會使用下列程式碼加入自訂的標頭：  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     您現在可以使用 XPath 篩選條件在訊息中檢查這個標頭，並且將包含標頭的訊息路由至 roundCalc 服務。  
  
2.  此外，路由服務會公開兩個虛擬服務端點，這兩個端點可以搭配使用 EndpointName、EndpointAddress 或 PrefixEndpointAddress 篩選條件，根據用戶端應用程式送出要求的目的地端點，透過唯一的方式將傳入訊息路由至特定的計算機實作。  
  
### <a name="define-endpoints"></a>若要定義端點  
  
1.  定義路由服務所使用的端點時，應該先判斷用戶端及服務所採用的通道型別。 在此案例中，兩個目的地服務皆使用要求-回覆模式，因此會使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。 下列範例定義路由服務所公開的服務端點。  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     路由服務會使用這個組態公開三個獨立的端點。 視執行階段選擇而定，用戶端應用程式會將訊息傳送至其中一個位址。 送達其中一個 （"rounding/calculator"或"regular/calculator"） 的 「 虛擬 」 服務端點的訊息都會轉送到對應的計算機實作。 如果用戶端應用程式不將要求傳送至特定的端點，訊息就會以一般端點為對象。 無論選擇何種端點，用戶端應用程式都可以選擇加入自訂標頭，表示應將訊息轉送至四捨五入計算機實作。  
  
2.  下列範例定義路由服務用來路由訊息的用戶端 (目的地) 端點。  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     篩選資料表中會使用這些端點表示訊息符合特定篩選條件時會送達的目的地端點。  
  
### <a name="define-filters"></a>若要定義篩選條件  
  
1.  若要將根據用戶端應用程式加入至訊息的"RoundingCalculator"自訂標頭的訊息路由，定義使用 XPath 查詢檢查此標頭存在的篩選。 因為此標頭利用自訂命名空間定義，也會加入可在 XPath 查詢中定義的 「 自訂 」 所使用的自訂命名空間前置詞的命名空間項目。 下列範例定義必要的路由區段、命名空間資料表，以及 XPath 篩選條件。  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     這**MessageFilter**尋找 RoundingCalculator 標頭中包含"rounding"值的訊息。 這個標頭是由用戶端設定的，用於指出應將訊息路由至 roundingCalc 服務。  
  
    > [!NOTE]
    >  S12 命名空間前置詞為預設會在命名空間資料表，且代表命名空間"http://www.w3.org/2003/05/soap-envelope"。  
  
2.  您必須同時設定會尋找兩個虛擬端點上接收到之訊息的篩選條件。 第一個虛擬端點是"regular/calculator"端點。 用戶端可以將要求傳送至這個端點，指出應將訊息路由至 regularCalc 服務。 下列組態定義的篩選條件會使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>，判斷訊息是否透過具有 filterData 中指定之名稱的端點送達。  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     如果名為"calculatorEndpoint"的服務端點所接收訊息時，此篩選條件會評估為`true`。  
  
3.  接下來，需要定義的篩選條件會尋找傳送至 roundingEndpoint 的位址之訊息。 用戶端可以將要求傳送至這個端點，指出應將訊息路由至 roundingCalc 服務。 下列設定會定義使用的篩選條件<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>來判斷訊息是否送達"rounding/calculator"端點。  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     如果在開頭的位址上收到的訊息 」http://localhost/routingservice/router/rounding/」 則此篩選條件評估為**true**。 此組態使用的基底位址，所以 「http://localhost/routingservice/router"和"rounding/calculator"roundingEndpoint 的指定的位址，用來與此端點通訊的完整位址是"http://localhost/routingservice/router/rounding/calculator"，其符合此篩選。  
  
    > [!NOTE]
    >  PrefixEndpointAddress 篩選條件執行比對時不會評估主機名稱，因為可以使用多種主機名稱 (均為從用戶端應用程式參考主機的有效方式) 參考單一主機。 例如，下列所有名稱皆可參考同一個主機：  
    >   
    >  -   localhost  
    > -   127.0.0.1  
    > -   www.contoso.com  
    > -   ContosoWeb01  
  
4.  最終的篩選條件必須支援路由送達一般端點 (沒有自訂標頭) 的訊息。 在這個案例中，訊息應在 regularCalc 和 roundingCalc 服務之間交替。 若要支援這些訊息的 「 循環配置資源 」 路由，使用自訂的篩選器可讓一個篩選條件執行個體，以符合每個訊息處理。  下列內容定義 RoundRobinMessageFilter 的兩個執行個體，這些執行個體群組在一起，表示應在彼此之間交替。  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     在執行階段時期，這個篩選條件類型會在所有已定義的此類型篩選執行個體之間交替 (這些執行個體已設定在一個集合的相同群組中)。 這樣可讓由這個自訂篩選條件處理的訊息在針對 RoundRobinFilter1 和 RoundRobinFilter2 傳回 `true` 之間交替。  
  
### <a name="define-filter-tables"></a>若要定義篩選資料表  
  
1.  若要將篩選條件與特定用戶端端點產生關聯，您必須將這些篩選條件置於篩選資料表中。 此範例案例也使用篩選條件優先順序設定，這是選擇性的設定，可讓您指出處理篩選條件的順序。 如果未指定篩選條件的優先順序，就會同時評估所有篩選條件。  
  
    > [!NOTE]
    >  指定篩選條件優先順序可以讓您控制處理篩選條件的順序，但這麼做可能會對路由服務的效能造成負面影響。 如果可行，請建構使用不需篩選條件優先順序的篩選條件邏輯。  
  
     下列範例定義篩選資料表並加入至具有優先順序為 2 的資料表先前定義的"XPathFilter"。 這個項目也指定是否"XPathFilter"符合訊息，訊息會路由至"roundingCalcEndpoint"  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     如果指定篩選條件優先順序，會先評估優先順序最高的篩選條件。 如果有一個或多個屬於特定優先順序層級的篩選條件相符，則不會評估優先順序層級較低的篩選條件。 在此案例中，2 是所指定的最高優先順序，也是這個層級唯一的篩選條件項目。  
  
2.  定義篩選條件項目是為了檢查端點名稱或位址前置詞，以確定特定端點是否已收到訊息。 下列項目會將這兩種篩選條件項目都加入到篩選資料表中，並且將它們與訊息的路由目的地端點產生關聯。 這些篩選條件的優先順序皆設定為 1，表示只有在前一個 XPath 篩選條件與訊息不相符時，這些篩選條件才能執行。  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     由於這些篩選條件的優先順序為 1，因此只有在優先順序層級 2 的篩選條件與訊息不相符時，才會評估這些篩選條件。 同時，由於兩種篩選條件的優先順序層級相同，因此會同時評估。 兩個篩選條件彼此互斥，所以只有其中一個會與訊息相符。  
  
3.  如果訊息不符合之前的所有篩選條件，就會透過泛型服務端點接收訊息，而且不會包含指出路由目的地的標頭資訊。 這些訊息會由自訂篩選條件處理，此篩選條件會在兩項計算機服務之間平衡這些訊息的負載。 下列範例示範如何在篩選資料表中加入篩選條件項目，其中每個篩選條件均與兩個目的地端點的其中之一產生關聯。  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     由於這些項目指定優先順序 0，因此只有在優先順序較高的篩選條件均與訊息不相符時，才會評估這些項目。 同時，由於兩種項目的優先順序相同，因此會同時評估。  
  
     如前所述，這些篩選條件定義所使用的自訂篩選條件只會將每個訊息所收到的其中一個篩選條件評估為 `true`。 由於只有兩個篩選條件是使用這個篩選條件所定義，而且指定了同樣的群組設定，因此，結果會是路由服務在傳送至 regularCalcEndpoint 及 RoundingCalcEndpoint 之間交替。  
  
4.  若要針對篩選條件評估訊息，必須先將篩選資料表關聯至要用於接收訊息的服務端點。  下列範例示範如何使用路由行為將路由資料表關聯至服務端點：  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>範例  
 下列範例是完整的組態檔清單。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [路由服務](../../../../docs/framework/wcf/samples/routing-services.md)
