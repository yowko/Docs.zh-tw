---
title: 如何：服務資料分割
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300381"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="d223e-102">如何：服務資料分割</span><span class="sxs-lookup"><span data-stu-id="d223e-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="d223e-103">本主題概要說明在相同目的地服務之多個執行個體中分割訊息所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="d223e-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="d223e-104">使用服務資料分割的時機，通常是在需要調整服務的規模以便提供更優良的服務品質，或是需要以某種特定的方式處理來自不同客戶的要求。</span><span class="sxs-lookup"><span data-stu-id="d223e-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="d223e-105">例如，從最高值或 「 金級 」 客戶的訊息可能需要處理更高的優先順序比標準客戶的訊息。</span><span class="sxs-lookup"><span data-stu-id="d223e-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="d223e-106">在此範例中，訊息會路由到 regularCalc 服務兩個執行個體的其中之一。</span><span class="sxs-lookup"><span data-stu-id="d223e-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="d223e-107">服務的兩個執行個體完全相同，但 calculator1 端點代表的服務會處理從高價值客戶接收到的訊息，而 calculator 2 端點則處理來自其他客戶的訊息。</span><span class="sxs-lookup"><span data-stu-id="d223e-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="d223e-108">從用戶端傳送的訊息沒有任何獨特的資料可用來識別應該將訊息路由到哪一個服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="d223e-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="d223e-109">為了協助各用戶端將資料路由到特定的目的地服務，我們會實作兩個服務端點，用來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d223e-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d223e-110">雖然這個範例使用特定的端點分割資料，但使用訊息本身內含的資訊 (例如標頭或本文資料)，也可以達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="d223e-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="d223e-111">實作服務資料分割</span><span class="sxs-lookup"><span data-stu-id="d223e-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="d223e-112">藉由指定服務所公開的服務端點，建立基本路由服務組態。</span><span class="sxs-lookup"><span data-stu-id="d223e-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="d223e-113">下列範例定義將用於接收訊息的兩個服務端點。</span><span class="sxs-lookup"><span data-stu-id="d223e-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="d223e-114">此外，也會定義用來傳送訊息至 regularCalc 服務執行個體的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="d223e-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="d223e-115">定義用於傳送訊息至目的地端點的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d223e-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="d223e-116">這個範例使用 EndpointName 篩選條件來判斷是哪一個服務端點接收到訊息。</span><span class="sxs-lookup"><span data-stu-id="d223e-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="d223e-117">下列範例定義必要的路由區段及篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d223e-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="d223e-118">定義篩選資料表，其使用用戶端端點關聯每個篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d223e-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="d223e-119">在此範例中，訊息將會根據接收到的特定端點安排路由。</span><span class="sxs-lookup"><span data-stu-id="d223e-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="d223e-120">由於訊息只可能符合兩項篩選條件的其中一項，因此不需要使用篩選條件優先順序來控制評估篩選條件的順序。</span><span class="sxs-lookup"><span data-stu-id="d223e-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="d223e-121">下列範例定義篩選資料表並加入先前定義的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d223e-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="d223e-122">若要針對包含在篩選資料表中的篩選評估傳入的訊息，您必須使用路由行為讓篩選資料表與服務端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d223e-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d223e-123">下列範例示範如何將"filterTable1"與服務端點：</span><span class="sxs-lookup"><span data-stu-id="d223e-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d223e-124">範例</span><span class="sxs-lookup"><span data-stu-id="d223e-124">Example</span></span>  
 <span data-ttu-id="d223e-125">下列範例是完整的組態檔清單。</span><span class="sxs-lookup"><span data-stu-id="d223e-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d223e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d223e-126">See also</span></span>

- [<span data-ttu-id="d223e-127">路由服務</span><span class="sxs-lookup"><span data-stu-id="d223e-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
