---
title: "HOW TO：服務版本控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
caps.latest.revision: 6
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 6
---
# HOW TO：服務版本控制
本主題概要說明建立路由組態服務時所需的基本步驟，該組態可傳送訊息至相同服務的不同版本。在此範例中，會將訊息傳送至兩個不同版本的計算器服務，`roundingCalc` \(v1\) 和 `regularCalc` \(v2\)。兩項實作都支援相同的作業，不過較舊的服務 `roundingCalc` 會在傳回之前將所有的計算結果捨入至最接近的整數值。用戶端應用程式必須能夠表示是否可使用較新的 `regularCalc` 服務。  
  
> [!WARNING]
>  為了傳送訊息至特定的服務版本，路由服務必須能夠根據訊息內容來判斷訊息的目的地。在以下呈現的方法中，用戶端會以插入資訊至訊息標頭的方法指定版本。也有某些服務版本的方法不需要用戶端傳送額外資料。例如，訊息可能被傳送至最近或相容性最高的服務版本，或者路由器會使用部分的標準 SOAP Envelope。  
  
 由這兩項服務公開的作業為：  
  
-   加  
  
-   減  
  
-   乘  
  
-   除  
  
 因為這兩項服務實作會處理相同的作業，而且它們與不是由其傳回的資料完全相同，所以包含在來自用戶端應用程式之訊息中的基底資料的唯一性質不足，無法藉此判斷路由要求方式。例如，無法使用動作篩選條件，因為兩項服務的預設動作均相同。  
  
 解決方法有數種，例如在路由器上為服務的每個版本公開特定的端點，或加入自訂標頭項目至訊息來表示服務版本。這幾個方法都可讓您以唯一的方式傳送傳入訊息至特定的服務版本，不過使用唯一的訊息內容是較好的方法，能夠區分不同服務版本間的要求。  
  
 在此範例中，用戶端應用程式會加入 ‘CalcVer’ 自訂標頭至要求訊息。此標頭會包含一個值，指示訊息應傳送至的服務版本。值 ‘1’ 代表訊息必須由 roundingCalc 服務加以處理，而值 ‘2’ 則代表由 regularCalc 服務來處理。此方法可讓用戶端應用程式直接控制要處理訊息的服務版本。自訂標頭是在訊息中的一個值，所以您可以使用一個端點來接收目的地為兩個服務版本的訊息。下列程式碼可用於用戶端應用程式中，以加入此自訂標頭至訊息：  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### 實作服務版本  
  
1.  藉由指定服務所公開的服務端點，建立基本路由服務組態。下列範例定義將用於接收訊息的單一服務端點。它也定義將用於傳送訊息至 `roundingCalc` \(v1\) 和 `regularCalc` \(v2\) 服務的用戶端端點。  
  
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
  
2.  定義用於傳送訊息至目的地端點的篩選條件。在此範例中，Xpath 篩選條件是用於偵測 “CalcVer” 自訂標頭的值，以判斷訊息要傳送至的版本。Xpath 篩選條件也可用於偵測未包含 “CalcVer” 標頭的訊息。下列範例定義必要的篩選條件和命名空間資料表。  
  
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
    >  s12 命名空間前置詞為命名空間資料表中的預設值，且代表命名空間 “http:\/\/www.w3.org\/2003\/05\/soap\-envelope”。  
  
3.  定義篩選資料表，其使用用戶端端點關聯每個篩選條件。如果訊息含有值為 1 的“CalcVer” 標頭，便會傳送訊息至 regularCalc 服務。如果標頭包含的值為 2，便會傳送標頭至 roundingCalc 服務。如果沒有標頭，則訊息會傳送至 regularCalc。  
  
     下列範例定義篩選資料表並加入先前定義的篩選條件。  
  
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
  
4.  若要針對包含在篩選資料表之篩選條件的傳入訊息加以評估，您必須使用路由行為產生篩選資料表與服務端點的關聯。下列範例呈現 “filterTable1” 與服務端點的關聯方法：  
  
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
  
## 範例  
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
  
## 範例  
 下列範例是完整的用戶端應用程式清單。  
  
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
  
## 請參閱  
 [路由服務](../../../../docs/framework/wcf/samples/routing-services.md)