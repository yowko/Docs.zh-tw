---
title: "HOW TO：服務版本控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4da80d264b05f9c7a1461a7298e521623a97f31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="b8fe0-102">HOW TO：服務版本控制</span><span class="sxs-lookup"><span data-stu-id="b8fe0-102">How To: Service Versioning</span></span>
<span data-ttu-id="b8fe0-103">本主題概要說明建立路由組態服務時所需的基本步驟，該組態可傳送訊息至相同服務的不同版本。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="b8fe0-104">在此範例中，會將訊息傳送至兩個不同版本的計算器服務，`roundingCalc` (v1) 和 `regularCalc` (v2)。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="b8fe0-105">兩項實作都支援相同的作業，不過較舊的服務 `roundingCalc` 會在傳回之前將所有的計算結果捨入至最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="b8fe0-106">用戶端應用程式必須能夠表示是否可使用較新的 `regularCalc` 服務。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b8fe0-107">為了傳送訊息至特定的服務版本，路由服務必須能夠根據訊息內容來判斷訊息的目的地。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="b8fe0-108">在以下呈現的方法中，用戶端會以插入資訊至訊息標頭的方法指定版本。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="b8fe0-109">也有某些服務版本的方法不需要用戶端傳送額外資料。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="b8fe0-110">例如，訊息可能被傳送至最近或相容性最高的服務版本，或者路由器會使用部分的標準 SOAP Envelope。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="b8fe0-111">由這兩項服務公開的作業為：</span><span class="sxs-lookup"><span data-stu-id="b8fe0-111">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="b8fe0-112">Add</span><span class="sxs-lookup"><span data-stu-id="b8fe0-112">Add</span></span>  
  
-   <span data-ttu-id="b8fe0-113">Subtract</span><span class="sxs-lookup"><span data-stu-id="b8fe0-113">Subtract</span></span>  
  
-   <span data-ttu-id="b8fe0-114">乘法</span><span class="sxs-lookup"><span data-stu-id="b8fe0-114">Multiply</span></span>  
  
-   <span data-ttu-id="b8fe0-115">分割</span><span class="sxs-lookup"><span data-stu-id="b8fe0-115">Divide</span></span>  
  
 <span data-ttu-id="b8fe0-116">因為這兩項服務實作會處理相同的作業，而且它們與不是由其傳回的資料完全相同，所以包含在來自用戶端應用程式之訊息中的基底資料的唯一性質不足，無法藉此判斷路由要求方式。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="b8fe0-117">例如，無法使用動作篩選條件，因為兩項服務的預設動作均相同。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="b8fe0-118">解決方法有數種，例如在路由器上為服務的每個版本公開特定的端點，或加入自訂標頭項目至訊息來表示服務版本。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="b8fe0-119">這幾個方法都可讓您以唯一的方式傳送傳入訊息至特定的服務版本，不過使用唯一的訊息內容是較好的方法，能夠區分不同服務版本間的要求。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="b8fe0-120">在此範例中，用戶端應用程式會加入 ‘CalcVer’ 自訂標頭至要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="b8fe0-121">此標頭會包含一個值，指示訊息應傳送至的服務版本。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="b8fe0-122">值 ‘1’ 代表訊息必須由 roundingCalc 服務加以處理，而值 ‘2’ 則代表由 regularCalc 服務來處理。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="b8fe0-123">此方法可讓用戶端應用程式直接控制要處理訊息的服務版本。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="b8fe0-124">自訂標頭是在訊息中的一個值，所以您可以使用一個端點來接收目的地為兩個服務版本的訊息。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="b8fe0-125">下列程式碼可用於用戶端應用程式中，以加入此自訂標頭至訊息：</span><span class="sxs-lookup"><span data-stu-id="b8fe0-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="b8fe0-126">實作服務版本</span><span class="sxs-lookup"><span data-stu-id="b8fe0-126">Implement Service Versioning</span></span>  
  
1.  <span data-ttu-id="b8fe0-127">藉由指定服務所公開的服務端點，建立基本路由服務組態。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="b8fe0-128">下列範例定義將用於接收訊息的單一服務端點。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="b8fe0-129">它也定義將用於傳送訊息至 `roundingCalc` (v1) 和 `regularCalc` (v2) 服務的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2.  <span data-ttu-id="b8fe0-130">定義用於傳送訊息至目的地端點的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="b8fe0-131">此範例中，XPath 篩選條件用於偵測"CalcVer"自訂標頭來判斷訊息應該路由傳送至哪一個版本的值。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="b8fe0-132">XPath 篩選條件也用於偵測未包含"CalcVer"標頭的訊息。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="b8fe0-133">下列範例定義必要的篩選條件和命名空間資料表。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b8fe0-134">S12 命名空間前置詞為預設會在命名空間資料表，且代表命名空間"http://www.w3.org/2003/05/soap-envelope"。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
3.  <span data-ttu-id="b8fe0-135">定義篩選資料表，其使用用戶端端點關聯每個篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="b8fe0-136">如果訊息包含"CalcVer"標頭的值為 1，則它會傳送至 regularCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="b8fe0-137">如果標頭包含的值為 2，便會傳送標頭至 roundingCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="b8fe0-138">如果沒有標頭，則訊息會傳送至 regularCalc。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="b8fe0-139">下列範例定義篩選資料表並加入先前定義的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="b8fe0-140">若要針對包含在篩選資料表之篩選條件的傳入訊息加以評估，您必須使用路由行為產生篩選資料表與服務端點的關聯。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="b8fe0-141">下列範例示範如何將"filterTable1"與服務端點：</span><span class="sxs-lookup"><span data-stu-id="b8fe0-141">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b8fe0-142">範例</span><span class="sxs-lookup"><span data-stu-id="b8fe0-142">Example</span></span>  
 <span data-ttu-id="b8fe0-143">下列範例是完整的組態檔清單。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-143">The following is a complete listing of the configuration file.</span></span>  
  
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
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="b8fe0-144">範例</span><span class="sxs-lookup"><span data-stu-id="b8fe0-144">Example</span></span>  
 <span data-ttu-id="b8fe0-145">下列範例是完整的用戶端應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="b8fe0-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to   
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8fe0-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8fe0-146">See Also</span></span>  
 [<span data-ttu-id="b8fe0-147">路由服務</span><span class="sxs-lookup"><span data-stu-id="b8fe0-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
