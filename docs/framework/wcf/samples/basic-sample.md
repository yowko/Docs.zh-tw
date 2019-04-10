---
title: 基本範例
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 1ceee6dd11b59ab9b43797ca8b1fd80c232fc8ea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327967"
---
# <a name="basic-sample"></a><span data-ttu-id="dbb32-102">基本範例</span><span class="sxs-lookup"><span data-stu-id="dbb32-102">Basic Sample</span></span>
<span data-ttu-id="dbb32-103">這個範例示範如何建立可探索的服務，以及如何搜尋和呼叫可探索的服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="dbb32-104">這個範例包含二個專案：服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="dbb32-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="dbb32-105">這個範例會在程式碼中實作探索。</span><span class="sxs-lookup"><span data-stu-id="dbb32-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="dbb32-106">如需在組態中實作探索的範例，請參閱 <<c0> [ 組態](../../../../docs/framework/wcf/samples/configuration-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="dbb32-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="dbb32-107">服務</span><span class="sxs-lookup"><span data-stu-id="dbb32-107">Service</span></span>  
 <span data-ttu-id="dbb32-108">這是簡單的計算機服務實作。</span><span class="sxs-lookup"><span data-stu-id="dbb32-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="dbb32-109">與探索相關的程式碼位於 `Main` 中，其中 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 會加入至服務主機，並且加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="dbb32-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="dbb32-110">用戶端</span><span class="sxs-lookup"><span data-stu-id="dbb32-110">Client</span></span>  
 <span data-ttu-id="dbb32-111">用戶端會使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 尋找服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="dbb32-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 是標準端點，會在用戶端開啟時解析服務的端點。</span><span class="sxs-lookup"><span data-stu-id="dbb32-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="dbb32-113">在此案例中，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 會根據服務合約尋找服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="dbb32-114">根據預設，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 會透過 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="dbb32-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="dbb32-115">一旦找到服務端點，用戶端就會透過指定的繫結連線到該服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="dbb32-116">用戶端會定義稱為 `InvokeCalculatorService` 的方法，該方法會使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="dbb32-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 繼承自 <xref:System.ServiceModel.Description.ServiceEndpoint>，因此可以傳遞至 `InvokeCalculatorService` 方法。</span><span class="sxs-lookup"><span data-stu-id="dbb32-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="dbb32-118">接著在範例中會使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 建立 `CalculatorServiceClient` 的執行個體，然後呼叫計算機服務的各項作業。</span><span class="sxs-lookup"><span data-stu-id="dbb32-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
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
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="dbb32-119">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="dbb32-119">To use this sample</span></span>  
  
1. <span data-ttu-id="dbb32-120">這個範例使用 HTTP 端點，若要執行這個範例，則必須加入正確的 URL ACL。</span><span class="sxs-lookup"><span data-stu-id="dbb32-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="dbb32-121">如需詳細資訊，請參閱 <<c0> [ 設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)。</span><span class="sxs-lookup"><span data-stu-id="dbb32-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="dbb32-122">以更高的權限執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="dbb32-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="dbb32-123">如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。</span><span class="sxs-lookup"><span data-stu-id="dbb32-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="dbb32-124">使用 Visual Studio 2012，開啟 Basic.sln 並建置範例。</span><span class="sxs-lookup"><span data-stu-id="dbb32-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>  
  
3. <span data-ttu-id="dbb32-125">執行 service.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbb32-125">Run the service.exe application.</span></span>  
  
4. <span data-ttu-id="dbb32-126">在啟動服務之後，執行 client.exe。</span><span class="sxs-lookup"><span data-stu-id="dbb32-126">After the service has started, run the client.exe.</span></span>  
  
5. <span data-ttu-id="dbb32-127">請注意，用戶端不需知道位址，就能找到此服務。</span><span class="sxs-lookup"><span data-stu-id="dbb32-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dbb32-128">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="dbb32-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dbb32-129">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="dbb32-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dbb32-130">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="dbb32-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbb32-131">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="dbb32-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
