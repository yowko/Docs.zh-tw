---
title: "HOW TO：以程式設計方式將探索能力加入 WCF 服務與用戶端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0a59788544a32b78e75ac25e787dcbae478451e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="3a73b-102">HOW TO：以程式設計方式將探索能力加入 WCF 服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="3a73b-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="3a73b-103">本主題將說明如何讓 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務成為可探索狀態。</span><span class="sxs-lookup"><span data-stu-id="3a73b-103">This topic explains how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span> <span data-ttu-id="3a73b-104">它基礎[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例。</span><span class="sxs-lookup"><span data-stu-id="3a73b-104">It is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="3a73b-105">若要為探索設定現有的自我裝載服務範例</span><span class="sxs-lookup"><span data-stu-id="3a73b-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="3a73b-106">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 [自我裝載] 方案。</span><span class="sxs-lookup"><span data-stu-id="3a73b-106">Open the Self-Host solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="3a73b-107">範例位於 TechnologySamples\Basic\Service\Hosting\SelfHost 目錄中。</span><span class="sxs-lookup"><span data-stu-id="3a73b-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="3a73b-108">將 `System.ServiceModel.Discovery.dll`的參考加入至服務專案。</span><span class="sxs-lookup"><span data-stu-id="3a73b-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="3a73b-109">您可能會看到下列錯誤訊息: 「 系統。</span><span class="sxs-lookup"><span data-stu-id="3a73b-109">You may see an error message saying "System.</span></span> <span data-ttu-id="3a73b-110">ServiceModel.Discovery.dll 或其中一個相依性需要較新版的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]比所指定的專案...」</span><span class="sxs-lookup"><span data-stu-id="3a73b-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …"</span></span> <span data-ttu-id="3a73b-111">如果您看到此訊息，以滑鼠右鍵按一下 方案總管 中的專案，然後選擇 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="3a73b-111">If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="3a73b-112">在**專案屬性**視窗中，請確定**目標 Framework**是[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3a73b-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="3a73b-113">開啟 Service.cs 檔案，然後加入下列 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a73b-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="3a73b-114">在 `Main()` 陳述式的 `using` 方法中，將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 執行個體加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="3a73b-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="3a73b-115"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 會指定所套用的服務成為可探索狀態。</span><span class="sxs-lookup"><span data-stu-id="3a73b-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="3a73b-116">在加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 程式碼的後方直接將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="3a73b-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="3a73b-117">此程式碼會指定探索訊息應傳送至標準 UDP 探索端點。</span><span class="sxs-lookup"><span data-stu-id="3a73b-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="3a73b-118">若要建立使用探索來呼叫服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="3a73b-118">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="3a73b-119">將新主控台應用程式加入至名為 `DiscoveryClientApp` 的方案。</span><span class="sxs-lookup"><span data-stu-id="3a73b-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="3a73b-120">將參考加入至 `System.ServiceModel.dll` 和 `System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="3a73b-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="3a73b-121">從現有的用戶端專案複製 GeneratedClient.cs 和 App.config 檔案並貼上至 DiscoveryClientApp 專案。</span><span class="sxs-lookup"><span data-stu-id="3a73b-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="3a73b-122">若要這樣做，請以滑鼠右鍵按一下中的檔案**方案總管 中**，選取**複製**，然後選取**DiscoveryClientApp**專案中，以滑鼠右鍵按一下並選取**貼上**。</span><span class="sxs-lookup"><span data-stu-id="3a73b-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="3a73b-123">開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="3a73b-123">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="3a73b-124">加入下列 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a73b-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="3a73b-125">將名為 `FindCalculatorServiceAddress()` 的靜態方法加入至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="3a73b-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="3a73b-126">這個方法會使用探索來搜尋 `CalculatorService` 服務。</span><span class="sxs-lookup"><span data-stu-id="3a73b-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="3a73b-127">在 `FindCalculatorServiceAddress` 方法中，建立新的 <xref:System.ServiceModel.Discovery.DiscoveryClient> 執行個體，傳入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 至建構函式。</span><span class="sxs-lookup"><span data-stu-id="3a73b-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="3a73b-128">這樣做可告知 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，<xref:System.ServiceModel.Discovery.DiscoveryClient> 類別應使用標準 UDP 探索端點來傳送和接收探索訊息。</span><span class="sxs-lookup"><span data-stu-id="3a73b-128">This tells [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="3a73b-129">在下一行，呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法並指定包含要搜尋之服務合約的 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a73b-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="3a73b-130">在此情況下，指定 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="3a73b-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="3a73b-131">呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 後，查看是否至少有一個符合的服務，然後傳回第一個符合服務的 <xref:System.ServiceModel.EndpointAddress>。</span><span class="sxs-lookup"><span data-stu-id="3a73b-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="3a73b-132">否則，傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="3a73b-132">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="3a73b-133">將名為 `InvokeCalculatorService` 的靜態方法加入至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="3a73b-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="3a73b-134">此方法使用自 `FindCalculatorServiceAddress` 傳回的端點位址來呼叫計算機服務。</span><span class="sxs-lookup"><span data-stu-id="3a73b-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="3a73b-135">在 `InvokeCalculatorService` 方法中，建立 `CalculatorServiceClient` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a73b-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="3a73b-136">這個類別由定義[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例。</span><span class="sxs-lookup"><span data-stu-id="3a73b-136">This class is defined by the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="3a73b-137">它是使用 Svcutil.exe 來產生的。</span><span class="sxs-lookup"><span data-stu-id="3a73b-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="3a73b-138">在下一行，將用戶端的端點位址設為從 `FindCalculatorServiceAddress()` 傳回的端點位址。</span><span class="sxs-lookup"><span data-stu-id="3a73b-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="3a73b-139">在前述的程式碼步驟之後，立即呼叫由計算機服務所公開的方法。</span><span class="sxs-lookup"><span data-stu-id="3a73b-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="3a73b-140">在 `Main()` 類別中將程式碼加入至  `Program` 方法來呼叫 `FindCalculatorServiceAddress`。</span><span class="sxs-lookup"><span data-stu-id="3a73b-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="3a73b-141">在下一行，呼叫 `InvokeCalculatorService()` 並傳入從 `FindCalculatorServiceAddress()` 傳回的端點位址。</span><span class="sxs-lookup"><span data-stu-id="3a73b-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="3a73b-142">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="3a73b-142">To test the application</span></span>  
  
1.  <span data-ttu-id="3a73b-143">開啟更高權限的命令提示字元，然後執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="3a73b-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="3a73b-144">開啟命令提示字元並執行 Discoveryclientapp.exe。</span><span class="sxs-lookup"><span data-stu-id="3a73b-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="3a73b-145">service.exe 的輸出應該看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="3a73b-145">The output from service.exe should look like the following output.</span></span>  
  
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
  
4.  <span data-ttu-id="3a73b-146">Discoveryclientapp.exe 的輸出應該看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="3a73b-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="3a73b-147">範例</span><span class="sxs-lookup"><span data-stu-id="3a73b-147">Example</span></span>  
 <span data-ttu-id="3a73b-148">以下是本範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="3a73b-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="3a73b-149">因為此程式碼根據[自我裝載](http://go.microsoft.com/fwlink/?LinkId=145523)範例，只會變更這些檔案會列出。</span><span class="sxs-lookup"><span data-stu-id="3a73b-149">Because this code is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="3a73b-150">自我裝載範例中，請參閱[安裝指示](http://go.microsoft.com/fwlink/?LinkId=145522)。</span><span class="sxs-lookup"><span data-stu-id="3a73b-150"> the Self-Host sample, see [Setup Instructions](http://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="3a73b-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a73b-151">See Also</span></span>  
 [<span data-ttu-id="3a73b-152">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="3a73b-152">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="3a73b-153">WCF 探索物件模型</span><span class="sxs-lookup"><span data-stu-id="3a73b-153">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
