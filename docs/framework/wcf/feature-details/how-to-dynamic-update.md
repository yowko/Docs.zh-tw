---
title: "HOW TO：動態更新"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 748286b4f6fa22b23423ff5c176c76d11fbe742d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="b13bf-102">HOW TO：動態更新</span><span class="sxs-lookup"><span data-stu-id="b13bf-102">How To: Dynamic Update</span></span>
<span data-ttu-id="b13bf-103">本主題概要說明建立和動態更新路由組態所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="b13bf-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="b13bf-104">在此範例中，初始路由組態是從組態檔取得，並且會將所有訊息路由傳送至 regularCalc 計算機服務。不過，該組態接著會以程式設計的方式更新，以變更 roundingCalc 服務的目的端點。</span><span class="sxs-lookup"><span data-stu-id="b13bf-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b13bf-105">在許多實作中，組態將完全為動態，而且不會倚賴預設組態。不過，在某些情況下，例如本主題中的情況，會希望服務啟動時為預設的組態狀態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b13bf-106">動態更新只會在記憶體中發生，而不會導致修改組態檔。</span><span class="sxs-lookup"><span data-stu-id="b13bf-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="b13bf-107">regularCalc 和 roundingCalc 兩者都支援相同的加、減、乘、除作業。不過，roundingCalc 會先將所有計算四捨五入至最接近的整數值再傳回。</span><span class="sxs-lookup"><span data-stu-id="b13bf-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="b13bf-108">組態檔可用來設定讓服務將所有訊息路由傳送至 regularCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="b13bf-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="b13bf-109">路由服務啟動後，<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> 可用來重新設定服務，使其將訊息路由傳送至 roundingCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="b13bf-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="b13bf-110">實作初始組態</span><span class="sxs-lookup"><span data-stu-id="b13bf-110">Implement Initial Configuration</span></span>  
  
1.  <span data-ttu-id="b13bf-111">藉由指定服務所公開的服務端點，建立基本路由服務組態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="b13bf-112">下列範例定義將用於接收訊息的單一服務端點。</span><span class="sxs-lookup"><span data-stu-id="b13bf-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="b13bf-113">此外，還會定義用來將訊息傳送至 regularCalc 的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="b13bf-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2.  <span data-ttu-id="b13bf-114">定義用於傳送訊息至目的地端點的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b13bf-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="b13bf-115">在此範例中，MatchAll 篩選條件會用來將所有訊息路由傳送至之前定義的 regularCalcEndpoint。</span><span class="sxs-lookup"><span data-stu-id="b13bf-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="b13bf-116">下列範例會定義篩選條件和篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="b13bf-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3.  <span data-ttu-id="b13bf-117">若要針對包含在篩選資料表之篩選條件的傳入訊息加以評估，您必須使用路由行為產生篩選資料表與服務端點的關聯。</span><span class="sxs-lookup"><span data-stu-id="b13bf-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="b13bf-118">下列範例示範如何將"filterTable1"與服務端點。</span><span class="sxs-lookup"><span data-stu-id="b13bf-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="b13bf-119">實作動態組態</span><span class="sxs-lookup"><span data-stu-id="b13bf-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="b13bf-120">路由服務的動態組態只能透過建立新的 <xref:System.ServiceModel.Routing.RoutingConfiguration>，並使用 <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> 取代目前組態的方式，在程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="b13bf-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="b13bf-121">在此範例中，路由服務會在主控台應用程式內自我裝載。</span><span class="sxs-lookup"><span data-stu-id="b13bf-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="b13bf-122">應用程式啟動後，您可以在主控台視窗中輸入 ‘regular’ 或 ‘rounding’ 來設定路由傳送訊息的目的端點，藉此修改路由組態。若輸入 ‘regular’ 則為 regularCalc，若輸入 ‘rounding’ 則為 roundingCalc。</span><span class="sxs-lookup"><span data-stu-id="b13bf-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1.  <span data-ttu-id="b13bf-123">必須加入以下 using 陳述式才能支援路由服務。</span><span class="sxs-lookup"><span data-stu-id="b13bf-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  <span data-ttu-id="b13bf-124">下列程式碼可用來自我裝載路由服務做為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b13bf-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="b13bf-125">這樣做會使用前一個步驟中描述的組態初始化路由服務，該組態包含在應用程式組態檔內。</span><span class="sxs-lookup"><span data-stu-id="b13bf-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="b13bf-126">while 迴圈包含的程式碼即可用來變更路由組態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners           
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="b13bf-127">若要動態更新路由組態，則必須建立新的路由組態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="b13bf-128">其中必須包含新路由組態需要的所有端點、篩選條件和篩選資料表，因為該組態會完全取代現有的路由組態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="b13bf-129">為了使用新的路由組態，您必須叫用 <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> 並且傳遞新的組態。</span><span class="sxs-lookup"><span data-stu-id="b13bf-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="b13bf-130">將下列程式碼加入至之前定義的 while 迴圈，即可根據使用者輸入重新設定服務。</span><span class="sxs-lookup"><span data-stu-id="b13bf-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b13bf-131">由於提供新 RoutingConfiguration 的方法包含在 RoutingExtension 服務延伸模組內，因此可以在擁有或能夠取得 ServiceHost 或 ServiceExtensions 參考 (例如在另一個 ServiceExtension 中) 的 WCF 擴充性模型中任何位置提供新的 RoutingConfiguration 物件。</span><span class="sxs-lookup"><span data-stu-id="b13bf-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span> <span data-ttu-id="b13bf-132">動態更新以這種方式 RoutingConfiguration 的範例，請參閱[動態重新設定](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md)。</span><span class="sxs-lookup"><span data-stu-id="b13bf-132">For an example of dynamically updating the RoutingConfiguration in this manner, see [Dynamic Reconfiguration](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b13bf-133">範例</span><span class="sxs-lookup"><span data-stu-id="b13bf-133">Example</span></span>  
 <span data-ttu-id="b13bf-134">以下是此範例中所使用主控台應用程式的完整清單。</span><span class="sxs-lookup"><span data-stu-id="b13bf-134">Following is a complete listing of the console application used in this example.</span></span>  
  
```  
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {             
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners           
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="b13bf-135">範例</span><span class="sxs-lookup"><span data-stu-id="b13bf-135">Example</span></span>  
 <span data-ttu-id="b13bf-136">以下是此範例中所使用組態檔的完整清單。</span><span class="sxs-lookup"><span data-stu-id="b13bf-136">Following is a complete listing of the configuration file used in this example.</span></span>  
  
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
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
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
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b13bf-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="b13bf-137">See Also</span></span>  
 [<span data-ttu-id="b13bf-138">路由服務</span><span class="sxs-lookup"><span data-stu-id="b13bf-138">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
