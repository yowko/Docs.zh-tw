---
title: 自我裝載
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 26a2cc6e7e4a023915f2e63009aa1570528cedf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964581"
---
# <a name="self-host"></a><span data-ttu-id="39112-102">自我裝載</span><span class="sxs-lookup"><span data-stu-id="39112-102">Self-Host</span></span>
<span data-ttu-id="39112-103">這個範例會示範如何在主控台應用程式中實作自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="39112-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="39112-104">這個範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="39112-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="39112-105">服務的組態檔已經從 Web.config 重新命名為 App.config，並且修改為設定主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="39112-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="39112-106">服務的原始程式碼已經修改為實作靜態 `Main` 函式，這個函式會建立和開啟提供已設定之基底位址的服務主機。</span><span class="sxs-lookup"><span data-stu-id="39112-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="39112-107">服務實作已經修改為將每個作業的輸出寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="39112-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="39112-108">除了設定服務的正確端點位址外，用戶端未經過修改。</span><span class="sxs-lookup"><span data-stu-id="39112-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39112-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="39112-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="39112-110">此範例會實作靜態的 main 函式，以便為指定的 <xref:System.ServiceModel.ServiceHost> 型別建立 `CalculatorService`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="39112-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="39112-111">當服務裝載於網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 時，服務的基底位址是由裝載環境提供。</span><span class="sxs-lookup"><span data-stu-id="39112-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="39112-112">在自我裝載案例中，您必須自行指定基底位址。</span><span class="sxs-lookup"><span data-stu-id="39112-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="39112-113">這項作業是使用`add`元素、 [ \<baseAddresses](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)的子系 >、 [ \<主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)的子系、 [ \<服務](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)的子系 > 如下列範例設定所示。</span><span class="sxs-lookup"><span data-stu-id="39112-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="39112-114">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="39112-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="39112-115">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="39112-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="39112-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="39112-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="39112-117">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="39112-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="39112-118">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="39112-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="39112-119">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="39112-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39112-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="39112-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="39112-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="39112-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="39112-122">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="39112-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39112-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="39112-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="39112-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39112-124">See also</span></span>

- [<span data-ttu-id="39112-125">AppFabric 裝載和持續性範例</span><span class="sxs-lookup"><span data-stu-id="39112-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
