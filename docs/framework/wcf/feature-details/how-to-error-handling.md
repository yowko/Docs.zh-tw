---
title: 如何：錯誤處理
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3752e358230b76d8984fa8e6a2ded43ad0eb2c6c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334987"
---
# <a name="how-to-error-handling"></a><span data-ttu-id="824c4-102">如何：錯誤處理</span><span class="sxs-lookup"><span data-stu-id="824c4-102">How To: Error Handling</span></span>
<span data-ttu-id="824c4-103">本主題概要說明建立使用錯誤處理的路由組態所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="824c4-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="824c4-104">在此範例中，訊息會路由傳送至目的地端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="824c4-105">如果訊息因為網路或通訊相關錯誤 (<xref:System.ServiceModel.CommunicationException>) 而無法傳遞，則會將訊息重新傳送至替代端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="824c4-106">為了模擬網路錯誤，此範例中使用的目的地端點包含了不正確的位址。</span><span class="sxs-lookup"><span data-stu-id="824c4-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="824c4-107">路由傳送至此端點的訊息會失敗，因為指定的位址上沒有接聽的服務。</span><span class="sxs-lookup"><span data-stu-id="824c4-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="824c4-108">雖然本主題中包含的範例未明確討論逾時設定，但是您在使用錯誤處理時，必須將逾時設定納入考量。</span><span class="sxs-lookup"><span data-stu-id="824c4-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="824c4-109">發生錯誤時，在用戶端接收回應之前會有另一項延遲發生。</span><span class="sxs-lookup"><span data-stu-id="824c4-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="824c4-110">這是因為路由服務收到錯誤，並接著嘗試將訊息傳送至備份端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="824c4-111">如果與主要和備份目的地端點相關聯的逾時值較長，用戶端可能經歷長時間的延遲，因為訊息成功傳送之前，在備份清單中的多個端點上失敗。</span><span class="sxs-lookup"><span data-stu-id="824c4-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="824c4-112">由於路由服務可能發生的最長延遲時間相當於與篩選相關聯之所有端點的逾時值總和，因此建議您與其對應並提高用戶端上預期的逾時。</span><span class="sxs-lookup"><span data-stu-id="824c4-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="824c4-113">實作錯誤處理</span><span class="sxs-lookup"><span data-stu-id="824c4-113">Implement Error Handling</span></span>  
  
1. <span data-ttu-id="824c4-114">藉由指定服務所公開的服務端點，建立基本路由服務組態。</span><span class="sxs-lookup"><span data-stu-id="824c4-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="824c4-115">下列範例定義會用於接收訊息的單一服務端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="824c4-116">此外，也會定義用來傳送訊息的用戶端端點 deadDestination 和 realDestination。</span><span class="sxs-lookup"><span data-stu-id="824c4-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="824c4-117">deadDestination 端點包含的位址不會參考執行中的服務，而且會在傳送訊息至此端點時，用來模擬網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="824c4-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2. <span data-ttu-id="824c4-118">定義用於傳送訊息至目的地端點的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="824c4-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="824c4-119">在此範例中，MatchAll 篩選會用來比對路由服務收到的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="824c4-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3. <span data-ttu-id="824c4-120">定義備份端點清單，當傳送至主要目的端點期間發生網路或通訊錯誤時，訊息會傳送至此清單中包含的備份端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="824c4-121">下列範例會定義包含一個端點的備份清單；不過，備份清單中可以指定多個端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="824c4-122">如果備份清單包含多個端點，當發生網路或通訊錯誤時，路由服務就會嘗試將訊息傳送至清單中的第一個端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="824c4-123">如果傳送至此端點時發生網路或通訊錯誤，路由服務會嘗試將訊息傳送至清單中包含的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="824c4-124">服務會繼續將訊息傳送至備份端點清單中的每一個端點，直到訊息傳送成功、所有備份端點都傳回網路或通訊相關錯誤，或是訊息已送出且端點傳回非網路、非通訊相關的錯誤為止。</span><span class="sxs-lookup"><span data-stu-id="824c4-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4. <span data-ttu-id="824c4-125">定義篩選資料表，該資料表會將篩選與 deadDestination 端點和備份端點清單產生關聯。</span><span class="sxs-lookup"><span data-stu-id="824c4-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="824c4-126">路由服務會先嘗試將訊息傳送至與篩選相關的目的地端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="824c4-127">由於 deadDestination 包含的位址不會參考執行中的服務，因此這樣會導致網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="824c4-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="824c4-128">路由服務接著會嘗試將訊息傳送至 backupEndpointlist 中指定的端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5. <span data-ttu-id="824c4-129">若要針對包含在篩選資料表中的篩選評估傳入的訊息，您必須使用路由行為讓篩選資料表與服務端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="824c4-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="824c4-130">下列範例示範如何將"filterTable1"與服務端點。</span><span class="sxs-lookup"><span data-stu-id="824c4-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="824c4-131">範例</span><span class="sxs-lookup"><span data-stu-id="824c4-131">Example</span></span>  
 <span data-ttu-id="824c4-132">以下為組態檔的完整清單。</span><span class="sxs-lookup"><span data-stu-id="824c4-132">Following is a complete listing of the configuration file.</span></span>  
  
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
            <!-- Add an entrty that maps the MatchAllMessageFilter to the dead destination -->  
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
