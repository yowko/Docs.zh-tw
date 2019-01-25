---
title: 如何：服務資料分割
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3755a9ecb61148bcc426e9d510dc2eab1c34eeb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590626"
---
# <a name="how-to-service-data-partitioning"></a>如何：服務資料分割
本主題概要說明在相同目的地服務之多個執行個體中分割訊息所需的基本步驟。 使用服務資料分割的時機，通常是在需要調整服務的規模以便提供更優良的服務品質，或是需要以某種特定的方式處理來自不同客戶的要求。 例如，從最高值或 「 金級 」 客戶的訊息可能需要處理更高的優先順序比標準客戶的訊息。  
  
 在此範例中，訊息會路由到 regularCalc 服務兩個執行個體的其中之一。 服務的兩個執行個體完全相同，但 calculator1 端點代表的服務會處理從高價值客戶接收到的訊息，而 calculator 2 端點則處理來自其他客戶的訊息。  
  
 從用戶端傳送的訊息沒有任何獨特的資料可用來識別應該將訊息路由到哪一個服務執行個體。 為了協助各用戶端將資料路由到特定的目的地服務，我們會實作兩個服務端點，用來接收訊息。  
  
> [!NOTE]
>  雖然這個範例使用特定的端點分割資料，但使用訊息本身內含的資訊 (例如標頭或本文資料)，也可以達成這個目的。  
  
### <a name="implement-service-data-partitioning"></a>實作服務資料分割  
  
1.  藉由指定服務所公開的服務端點，建立基本路由服務組態。 下列範例定義將用於接收訊息的兩個服務端點。 此外，也會定義用來傳送訊息至 regularCalc 服務執行個體的用戶端端點。  
  
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
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2.  定義用於傳送訊息至目的地端點的篩選條件。  這個範例使用 EndpointName 篩選條件來判斷是哪一個服務端點接收到訊息。 下列範例定義必要的路由區段及篩選條件。  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3.  定義篩選資料表，其使用用戶端端點關聯每個篩選條件。 在此範例中，訊息將會根據接收到的特定端點安排路由。 由於訊息只可能符合兩項篩選條件的其中一項，因此不需要使用篩選條件優先順序來控制評估篩選條件的順序。  
  
     下列範例定義篩選資料表並加入先前定義的篩選條件。  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  若要針對包含在篩選資料表中的篩選評估傳入的訊息，您必須使用路由行為讓篩選資料表與服務端點產生關聯。 下列範例示範如何將"filterTable1"與服務端點：  
  
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
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱
- [路由服務](../../../../docs/framework/wcf/samples/routing-services.md)
