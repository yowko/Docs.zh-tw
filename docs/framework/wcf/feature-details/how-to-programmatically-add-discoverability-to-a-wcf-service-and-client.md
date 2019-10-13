---
title: 作法：以程式設計方式將探索能力新增至 WCF 服務與用戶端
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a139eb4a15486be329bc6853ee6b3a3be06b0619
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291566"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>作法：以程式設計方式將探索能力新增至 WCF 服務與用戶端
本主題說明如何讓 Windows Communication Foundation （WCF）服務可供探索。 它是以[自我裝載](https://go.microsoft.com/fwlink/?LinkId=145523)範例為基礎。  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>若要為探索設定現有的自我裝載服務範例  
  
1. 在 Visual Studio 2012 中開啟自我裝載解決方案。 範例位於 TechnologySamples\Basic\Service\Hosting\SelfHost 目錄中。  
  
2. 將 `System.ServiceModel.Discovery.dll`的參考加入至服務專案。 您可能會看到指出「系統」的錯誤訊息。 System.servicemodel 或它的其中一個相依性需要較新版本的 .NET Framework，而不是專案中所指定的版本 ...」如果您看到此訊息，請以滑鼠右鍵按一下 方案總管中的專案，然後選擇 **屬性**。 在 [**專案屬性**] 視窗中，確定**目標 Framework**為 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]。  
  
3. 開啟 Service.cs 檔案，然後加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. 在 `Main()` 陳述式的 `using` 方法中，將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 執行個體加入至服務主機。  
  
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
  
5. 在加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 程式碼的後方直接將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機。  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     此程式碼會指定探索訊息應傳送至標準 UDP 探索端點。  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>若要建立使用探索來呼叫服務的用戶端應用程式  
  
1. 將新主控台應用程式加入至名為 `DiscoveryClientApp` 的方案。  
  
2. 將參考加入至 `System.ServiceModel.dll` 和 `System.ServiceModel.Discovery.dll`  
  
3. 從現有的用戶端專案複製 GeneratedClient.cs 和 App.config 檔案並貼上至 DiscoveryClientApp 專案。 若要這麼做，請以滑鼠右鍵按一下**方案總管**中的檔案，選取 [**複製**]，然後選取**discoveryclientapp.exe**專案，按一下滑鼠右鍵並選取 [**貼**上]。  
  
4. 開啟 Program.cs。  
  
5. 加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. 將名為 `FindCalculatorServiceAddress()` 的靜態方法加入至 `Program` 類別。  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     這個方法會使用探索來搜尋 `CalculatorService` 服務。  
  
7. 在 `FindCalculatorServiceAddress` 方法中，建立新的 <xref:System.ServiceModel.Discovery.DiscoveryClient> 執行個體，傳入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 至建構函式。  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     這會告訴 WCF @no__t 0 類別應該使用標準 UDP 探索端點來傳送和接收探索訊息。  
  
8. 在下一行，呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法並指定包含要搜尋之服務合約的 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體。 在此情況下，指定 `ICalculator`。  
  
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
  
11. 在 `InvokeCalculatorService` 方法中，建立 `CalculatorServiceClient` 類別的執行個體。 此類別是由[自我裝載](https://go.microsoft.com/fwlink/?LinkId=145523)範例所定義。 它是使用 Svcutil.exe 來產生的。  
  
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
  
1. 開啟更高權限的命令提示字元，然後執行 Service.exe。  
  
2. 開啟命令提示字元並執行 Discoveryclientapp.exe。  
  
3. service.exe 的輸出應該看起來如下所示。  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. Discoveryclientapp.exe 的輸出應該看起來如下所示。  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>範例  
 以下是本範例的程式碼清單。 因為此程式碼是以[自我裝載](https://go.microsoft.com/fwlink/?LinkId=145523)範例為基礎，所以只會列出已變更的檔案。 如需有關自我裝載範例的詳細資訊，請參閱[設定指示](https://go.microsoft.com/fwlink/?LinkId=145522)。  
  
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

- [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [WCF 探索物件模型](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
