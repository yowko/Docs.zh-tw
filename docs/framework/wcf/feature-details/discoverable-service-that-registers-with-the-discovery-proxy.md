---
title: "HOW TO：實作以探索 Proxy 註冊的可探索服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee99c7c74f0e1e2d287802d46cf4b716cfa3b76d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="a49b2-102">HOW TO：實作以探索 Proxy 註冊的可探索服務</span><span class="sxs-lookup"><span data-stu-id="a49b2-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="a49b2-103">本主題是四個主題中的第二個，討論如何實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="a49b2-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="a49b2-104">在先前的主題， [How to： 實作探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)，實作探索 proxy。</span><span class="sxs-lookup"><span data-stu-id="a49b2-104">In the previous topic, [How to: Implement a Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="a49b2-105">在這個主題中，您會建立一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，這個服務會傳送公告訊息 (`Hello` 和 `Bye`) 至探索 Proxy，使其向探索 Proxy 註冊和取消註冊其本身。</span><span class="sxs-lookup"><span data-stu-id="a49b2-105">In this topic, you create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="a49b2-106">若要定義服務合約</span><span class="sxs-lookup"><span data-stu-id="a49b2-106">To define the service contract</span></span>  
  
1.  <span data-ttu-id="a49b2-107">將新的主控台應用程式專案加入至名為 `DiscoveryProxyExample` 的 `Service` 方案。</span><span class="sxs-lookup"><span data-stu-id="a49b2-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>  
  
2.  <span data-ttu-id="a49b2-108">加入下列組件的參考：</span><span class="sxs-lookup"><span data-stu-id="a49b2-108">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="a49b2-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a49b2-109">System.ServiceModel</span></span>  
  
    2.  <span data-ttu-id="a49b2-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="a49b2-110">System.ServiceModel.Discovery</span></span>  
  
3.  <span data-ttu-id="a49b2-111">將新的類別加入至名為 `CalculatorService` 的專案。</span><span class="sxs-lookup"><span data-stu-id="a49b2-111">Add a new class to the project called `CalculatorService`.</span></span>  
  
4.  <span data-ttu-id="a49b2-112">使用陳述式加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a49b2-112">Add the following using statements.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
5.  <span data-ttu-id="a49b2-113">在 CalculatorService.cs 內定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="a49b2-113">Within CalculatorService.cs, define the service contract.</span></span>  
  
    ```csharp  
    // Define a service contract.  
        [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]  
        public interface ICalculatorService  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
    ```  
  
6.  <span data-ttu-id="a49b2-114">同樣地，在 CalculatorService.cs 內實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="a49b2-114">Also within CalculatorService.cs, implement the service contract.</span></span>  
  
    ```csharp  
    // Service class which implements the service contract.      
        public class CalculatorService : ICalculatorService  
        {  
            public double Add(double n1, double n2)  
            {  
                double result = n1 + n2;  
                Console.WriteLine("Received Add({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Subtract(double n1, double n2)  
            {  
                double result = n1 - n2;  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Multiply(double n1, double n2)  
            {  
                double result = n1 * n2;  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Divide(double n1, double n2)  
            {  
                double result = n1 / n2;  
                Console.WriteLine("Received Divide({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
        }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="a49b2-115">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="a49b2-115">To host the service</span></span>  
  
1.  <span data-ttu-id="a49b2-116">開啟當您建立專案時產生的 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="a49b2-116">Open the Program.cs file that was generated when you created the project.</span></span>  
  
2.  <span data-ttu-id="a49b2-117">使用陳述式加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a49b2-117">Add the following using statements.</span></span>  
  
    ```csharp 
    using System;  
    using System.ServiceModel;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Discovery;  
    ```  
  
3.  <span data-ttu-id="a49b2-118">在 `Main()` 方法內加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a49b2-118">Within the `Main()` method, add the following code:</span></span>  
  
    ```csharp  
    // Define the base address of the service  
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());  
    // Define the endpoint address where announcement messages will be sent  
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
    // Create the service host  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    try  
    {  
       // Add a service endpoint  
       ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
       // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
       AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
  
       // Create a ServiceDiscoveryBehavior and add the announcement endpoint  
       ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
                    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);  
  
       // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable  
       serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);  
  
       // Start listening for messages  
      serviceHost.Open();  
  
       Console.WriteLine("Calculator Service started at {0}", baseAddress);  
       Console.WriteLine();  
       Console.WriteLine("Press <ENTER> to terminate the service.");  
       Console.WriteLine();  
       Console.ReadLine();  
  
       serviceHost.Close();  
    }  
    catch (CommunicationException e)  
    {  
       Console.WriteLine(e.Message);  
    }  
    catch (TimeoutException e)  
    {  
       Console.WriteLine(e.Message);  
    }     
  
    if (serviceHost.State != CommunicationState.Closed)  
    {  
       Console.WriteLine("Aborting the service...");  
       serviceHost.Abort();  
    }  
    ```  
  
 <span data-ttu-id="a49b2-119">您已經完成實作可探索的服務。</span><span class="sxs-lookup"><span data-stu-id="a49b2-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="a49b2-120">繼續前往[How to： 實作使用探索 Proxy 來尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a49b2-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a49b2-121">範例</span><span class="sxs-lookup"><span data-stu-id="a49b2-121">Example</span></span>  
 <span data-ttu-id="a49b2-122">以下是本主題所使用之程式碼的完整清單。</span><span class="sxs-lookup"><span data-stu-id="a49b2-122">This is the full listing of the code used in this topic.</span></span>  
  
```csharp  
// CalculatorService.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
  
namespace Microsoft.Samples.Discovery  
{  
    // Define a service contract.  
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]  
    public interface ICalculatorService  
    {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
  
    // Service class which implements the service contract.      
    public class CalculatorService : ICalculatorService  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Program  
    {  
        public static void Main()  
        {  
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());  
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
            try  
            {  
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);  
  
                // Make the service discoverable  
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);  
  
                serviceHost.Open();  
  
                Console.WriteLine("Calculator Service started at {0}", baseAddress);  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to terminate the service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                serviceHost.Close();  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            catch (TimeoutException e)  
            {  
                Console.WriteLine(e.Message);  
            }     
  
            if (serviceHost.State != CommunicationState.Closed)  
            {  
                Console.WriteLine("Aborting the service...");  
                serviceHost.Abort();  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="a49b2-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="a49b2-123">See Also</span></span>  
 [<span data-ttu-id="a49b2-124">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="a49b2-124">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="a49b2-125">如何：實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="a49b2-125">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="a49b2-126">如何：實作使用探索 Proxy 搜尋服務的用戶端應用程式來尋找服務</span><span class="sxs-lookup"><span data-stu-id="a49b2-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
