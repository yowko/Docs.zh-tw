---
title: HOW TO：使用 Windows Communication Foundation 用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 6667a8e9862054d7d8d5b20e70dfbe699de02eab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>HOW TO：使用 Windows Communication Foundation 用戶端
這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六個工作的最後一個。 六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 一旦已建立並設定 Windows Communication Foundation (WCF) proxy，可以建立用戶端執行個體和用戶端應用程式可編譯及用來與通訊[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務。 本主題將說明具現化及使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的程序。 這個程序會執行三項工作：  
  
1.  具現化 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端。  
  
2.  從產生的 Proxy 呼叫服務作業。  
  
3.  在完成作業呼叫後即關閉用戶端。  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>若要使用 Windows Communication Foundation 用戶端  
  
1.  開啟 GettingStartedClient 專案中的 Program.cs 或 Program.vb 檔案，並以下列程式碼取代現有的程式碼：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
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
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     注意匯入 GettingStartedClient.ServiceReference1 的 using 或 imports 陳述式。 這會匯入在 Visual Studio 中 [加入服務參考] 所產生的程式碼。 程式碼會具現化 WCF Proxy，然後呼叫計算機服務所公開的每一項服務作業、關閉 Proxy 並終止。  
  
 您現在已完成教學課程。 您定義服務合約、實作服務合約、產生 WCF Proxy、設定 WCF 用戶端應用程式，然後使用 Proxy 來呼叫服務作業。 若要測試應用程式，請先執行 GettingStartedHost 以啟動服務，然後再執行 GettingStartedClient。 GettingStartedHost 的輸出應該看起來像這樣：  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 GettingStartedClient 的輸出應該看起來像這樣：  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>另請參閱  
 [建置用戶端](../../../docs/framework/wcf/building-clients.md)  
 [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [如何：建立雙面合約](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [如何：使用雙面合約存取服務](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
