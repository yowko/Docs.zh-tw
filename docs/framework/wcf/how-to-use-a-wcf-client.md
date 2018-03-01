---
title: "HOW TO：使用 Windows Communication Foundation 用戶端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0330c386730c6b0436196bb5b85162bc4621c214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="e2d9f-102">HOW TO：使用 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="e2d9f-102">How to: Use a Windows Communication Foundation Client</span></span>
<span data-ttu-id="e2d9f-103">這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六個工作中的最後一個。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-103">This is the last of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="e2d9f-104">六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="e2d9f-105">在建立並設定 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Proxy 之後，就可以建立用戶端執行個體，也可以編譯用戶端應用程式並用於與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務通訊。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-105">Once a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="e2d9f-106">本主題將說明具現化及使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的程序。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-106">This topic describes procedures for instantiating and using a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="e2d9f-107">這個程序會執行三項工作：</span><span class="sxs-lookup"><span data-stu-id="e2d9f-107">This procedure does three things:</span></span>  
  
1.  <span data-ttu-id="e2d9f-108">具現化 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-108">Instantiates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
2.  <span data-ttu-id="e2d9f-109">從產生的 Proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-109">Calls the service operations from the generated proxy.</span></span>  
  
3.  <span data-ttu-id="e2d9f-110">在完成作業呼叫後即關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-110">Closes the client once the operation call is completed.</span></span>  
  
### <a name="to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="e2d9f-111">若要使用 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="e2d9f-111">To use a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="e2d9f-112">開啟 GettingStartedClient 專案中的 Program.cs 或 Program.vb 檔案，並以下列程式碼取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="e2d9f-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>  
  
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
  
     <span data-ttu-id="e2d9f-113">注意匯入 GettingStartedClient.ServiceReference1 的 using 或 imports 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-113">Notice the using or imports statement that imports the GettingStartedClient.ServiceReference1.</span></span> <span data-ttu-id="e2d9f-114">這會匯入在 Visual Studio 中 [加入服務參考] 所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-114">This imports the code generated by Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="e2d9f-115">程式碼會具現化 WCF Proxy，然後呼叫計算機服務所公開的每一項服務作業、關閉 Proxy 並終止。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy and terminates.</span></span>  
  
 <span data-ttu-id="e2d9f-116">您現在已完成教學課程。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-116">You have now completed the tutorial.</span></span> <span data-ttu-id="e2d9f-117">您定義服務合約、實作服務合約、產生 WCF Proxy、設定 WCF 用戶端應用程式，然後使用 Proxy 來呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="e2d9f-118">若要測試應用程式，請先執行 GettingStartedHost 以啟動服務，然後再執行 GettingStartedClient。</span><span class="sxs-lookup"><span data-stu-id="e2d9f-118">To test out the application first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span> <span data-ttu-id="e2d9f-119">GettingStartedHost 的輸出應該看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="e2d9f-119">The output from GettingStartedHost should look like this:</span></span>  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 <span data-ttu-id="e2d9f-120">GettingStartedClient 的輸出應該看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="e2d9f-120">The output from GettingStartedClient should look like this:</span></span>  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2d9f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2d9f-121">See Also</span></span>  
 [<span data-ttu-id="e2d9f-122">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="e2d9f-122">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="e2d9f-123">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="e2d9f-123">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="e2d9f-124">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="e2d9f-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="e2d9f-125">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="e2d9f-125">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="e2d9f-126">如何：建立雙面合約</span><span class="sxs-lookup"><span data-stu-id="e2d9f-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="e2d9f-127">如何：使用雙面合約存取服務</span><span class="sxs-lookup"><span data-stu-id="e2d9f-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="e2d9f-128">快速入門</span><span class="sxs-lookup"><span data-stu-id="e2d9f-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="e2d9f-129">自我裝載</span><span class="sxs-lookup"><span data-stu-id="e2d9f-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
