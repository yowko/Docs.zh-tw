---
title: HOW TO：以程式設計方式將探索能力加入 WCF 服務與用戶端
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 0685694db8f67ed690cf2a8002bf70a05695a192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495479"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>HOW TO：以程式設計方式將探索能力加入 WCF 服務與用戶端
本主題說明如何讓 Windows Communication Foundation (WCF) 服務可以探索。 它基礎[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例。  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>若要為探索設定現有的自我裝載服務範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 [自我裝載] 方案。 範例位於 TechnologySamples\Basic\Service\Hosting\SelfHost 目錄中。  
  
2.  將 `System.ServiceModel.Discovery.dll`的參考加入至服務專案。 您可能會看到下列錯誤訊息: 「 系統。 ServiceModel.Discovery.dll 或其中一個相依性需要較新版的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]比所指定的專案...」 如果您看到此訊息，以滑鼠右鍵按一下 方案總管 中的專案，然後選擇 **屬性**。 在**專案屬性**視窗中，請確定**目標 Framework**是[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]。  
  
3.  開啟 Service.cs 檔案，然後加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  在 `Main()` 陳述式的 `using` 方法中，將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 執行個體加入至服務主機。  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
  
            // ...  
        }  
    }  
    ```  
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 會指定所套用的服務成為可探索狀態。  
  
5.  在加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 程式碼的後方直接將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機。  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     此程式碼會指定探索訊息應傳送至標準 UDP 探索端點。  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>若要建立使用探索來呼叫服務的用戶端應用程式  
  
1.  將新主控台應用程式加入至名為 `DiscoveryClientApp` 的方案。  
  
2.  將參考加入至 `System.ServiceModel.dll` 和 `System.ServiceModel.Discovery.dll`  
  
3.  從現有的用戶端專案複製 GeneratedClient.cs 和 App.config 檔案並貼上至 DiscoveryClientApp 專案。 若要這樣做，請以滑鼠右鍵按一下中的檔案**方案總管 中**，選取**複製**，然後選取**DiscoveryClientApp**專案中，以滑鼠右鍵按一下並選取**貼上**。  
  
4.  開啟 Program.cs。  
  
5.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  將名為 `FindCalculatorServiceAddress()` 的靜態方法加入至 `Program` 類別。  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     這個方法會使用探索來搜尋 `CalculatorService` 服務。  
  
7.  在 `FindCalculatorServiceAddress` 方法中，建立新的 <xref:System.ServiceModel.Discovery.DiscoveryClient> 執行個體，傳入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 至建構函式。  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     這會告知 WCF，<xref:System.ServiceModel.Discovery.DiscoveryClient>類別應該用來傳送和接收探索訊息的標準 UDP 探索端點。  
  
8.  在下一行，呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法並指定包含要搜尋之服務合約的 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體。 在此情況下，指定 `ICalculator`。  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. 呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 後，查看是否至少有一個符合的服務，然後傳回第一個符合服務的 <xref:System.ServiceModel.EndpointAddress>。 否則，傳回 `null`。  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. 將名為 `InvokeCalculatorService` 的靜態方法加入至 `Program` 類別。  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     此方法使用自 `FindCalculatorServiceAddress` 傳回的端點位址來呼叫計算機服務。  
  
11. 在 `InvokeCalculatorService` 方法中，建立 `CalculatorServiceClient` 類別的執行個體。 這個類別由定義[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例。 它是使用 Svcutil.exe 來產生的。  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. 在下一行，將用戶端的端點位址設為從 `FindCalculatorServiceAddress()` 傳回的端點位址。  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. 在前述的程式碼步驟之後，立即呼叫由計算機服務所公開的方法。  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. 在 `Main()` 類別中將程式碼加入至  `Program` 方法來呼叫 `FindCalculatorServiceAddress`。  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. 在下一行，呼叫 `InvokeCalculatorService()` 並傳入從 `FindCalculatorServiceAddress()` 傳回的端點位址。  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  開啟更高權限的命令提示字元，然後執行 Service.exe。  
  
2.  開啟命令提示字元並執行 Discoveryclientapp.exe。  
  
3.  service.exe 的輸出應該看起來如下所示。  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  Discoveryclientapp.exe 的輸出應該看起來如下所示。  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>範例  
 以下是本範例的程式碼清單。 因為此程式碼根據[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例，只會變更這些檔案會列出。 如需自我裝載範例的詳細資訊，請參閱[安裝指示](http://go.microsoft.com/fwlink/?LinkId=145522)。  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints              
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a>另請參閱  
 [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [WCF 探索物件模型](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
