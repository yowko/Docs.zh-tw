---
title: 執行個體
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 37ffbe36b231737ca10b2dc864ad6e5b304b94bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648309"
---
# <a name="instancing"></a><span data-ttu-id="ff031-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="ff031-102">Instancing</span></span>
<span data-ttu-id="ff031-103">執行個體範例會示範執行個體行為設定，此設定會控制如何建立可回應用戶端需求的服務類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff031-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="ff031-104">此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。</span><span class="sxs-lookup"><span data-stu-id="ff031-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="ff031-105">這個範例會定義繼承自 `ICalculatorInstance` 的新合約 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="ff031-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="ff031-106">由 `ICalculatorInstance` 指定的合約會提供三種額外作業以檢查服務執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="ff031-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="ff031-107">藉由改變執行個體設定，您可以在執行用戶端時觀察行為上的改變。</span><span class="sxs-lookup"><span data-stu-id="ff031-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="ff031-108">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="ff031-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff031-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ff031-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ff031-110">以下為可用的執行個體模式：</span><span class="sxs-lookup"><span data-stu-id="ff031-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="ff031-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>：針對每個用戶端要求建立新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff031-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="ff031-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>：新執行個體是針對每個新的用戶端工作階段中，建立和維護 （需要支援工作階段的繫結） 該工作階段的存留期。</span><span class="sxs-lookup"><span data-stu-id="ff031-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="ff031-113"><xref:System.ServiceModel.InstanceContextMode.Single>：單一執行個體的服務類別會處理所有的用戶端要求應用程式的存留期。</span><span class="sxs-lookup"><span data-stu-id="ff031-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="ff031-114">此服務類別會指定具有 `[ServiceBehavior(InstanceContextMode=<setting>)]` 屬性的執行個體行為，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="ff031-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="ff031-115">藉由將程式碼行標記為註解，您便可以觀察到每個執行個體模式的行為。</span><span class="sxs-lookup"><span data-stu-id="ff031-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="ff031-116">請記得在變更執行個體模式後重建服務。</span><span class="sxs-lookup"><span data-stu-id="ff031-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="ff031-117">這時並不需要在用戶端上指定任何與執行個體相關的設定。</span><span class="sxs-lookup"><span data-stu-id="ff031-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="ff031-118">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ff031-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ff031-119">服務正在執行的執行個體模式會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="ff031-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="ff031-120">在完成每個作業後，會顯示執行個體識別碼與作業計數以反映執行個體模式的行為。</span><span class="sxs-lookup"><span data-stu-id="ff031-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="ff031-121">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff031-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ff031-122">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ff031-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ff031-123">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ff031-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ff031-124">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ff031-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ff031-125">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ff031-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff031-126">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ff031-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff031-127">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ff031-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff031-128">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ff031-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff031-129">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ff031-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
