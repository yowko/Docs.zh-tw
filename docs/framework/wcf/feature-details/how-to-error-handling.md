---
title: 如何：錯誤處理
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3b8e48a74ff7671b942b5499fb3a0b5d0f389d61
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834705"
---
# <a name="how-to-error-handling"></a>如何：錯誤處理

本主題概要說明建立使用錯誤處理的路由組態所需的基本步驟。 在此範例中，訊息會路由傳送至目的地端點。 如果訊息因為網路或通訊相關錯誤 (<xref:System.ServiceModel.CommunicationException>) 而無法傳遞，則會將訊息重新傳送至替代端點。

> [!NOTE]
> 為了模擬網路錯誤，此範例中使用的目的地端點包含了不正確的位址。 路由傳送至此端點的訊息會失敗，因為指定的位址上沒有接聽的服務。

> [!NOTE]
> 雖然本主題中包含的範例未明確討論逾時設定，但是您在使用錯誤處理時，必須將逾時設定納入考量。 發生錯誤時，在用戶端接收回應之前會有另一項延遲發生。 這是因為路由服務收到錯誤，並接著嘗試將訊息傳送至備份端點。 如果與主要和備份目的地端點相關聯的逾時值較長，用戶端可能經歷長時間的延遲，因為訊息成功傳送之前，在備份清單中的多個端點上失敗。
>
> 由於路由服務可能發生的最長延遲時間相當於與篩選相關聯之所有端點的逾時值總和，因此建議您與其對應並提高用戶端上預期的逾時。

### <a name="implement-error-handling"></a>實作錯誤處理

1. 藉由指定服務所公開的服務端點，建立基本路由服務組態。 下列範例定義會用於接收訊息的單一服務端點。 此外，也會定義用來傳送訊息的用戶端端點 deadDestination 和 realDestination。 deadDestination 端點包含的位址不會參考執行中的服務，而且會在傳送訊息至此端點時，用來模擬網路錯誤。

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. 定義用於傳送訊息至目的地端點的篩選條件。  在此範例中，MatchAll 篩選會用來比對路由服務收到的所有訊息。

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. 定義備份端點清單，當傳送至主要目的端點期間發生網路或通訊錯誤時，訊息會傳送至此清單中包含的備份端點。 下列範例會定義包含一個端點的備份清單；不過，備份清單中可以指定多個端點。

     如果備份清單包含多個端點，當發生網路或通訊錯誤時，路由服務就會嘗試將訊息傳送至清單中的第一個端點。 如果傳送至此端點時發生網路或通訊錯誤，路由服務會嘗試將訊息傳送至清單中包含的下一個端點。 服務會繼續將訊息傳送至備份端點清單中的每一個端點，直到訊息傳送成功、所有備份端點都傳回網路或通訊相關錯誤，或是訊息已送出且端點傳回非網路、非通訊相關的錯誤為止。

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. 定義篩選資料表，該資料表會將篩選與 deadDestination 端點和備份端點清單產生關聯。  路由服務會先嘗試將訊息傳送至與篩選相關的目的地端點。 由於 deadDestination 包含的位址不會參考執行中的服務，因此這樣會導致網路錯誤。 然後，路由服務會嘗試將訊息傳送至 backupEndpointList 中指定的端點。

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. 若要針對包含在篩選資料表中的篩選評估傳入的訊息，您必須使用路由行為讓篩選資料表與服務端點產生關聯。  下列範例示範如何將 "filterTable1" 與服務端點產生關聯。

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>範例

以下是完整的配置檔案清單：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
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
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```
