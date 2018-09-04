---
title: 節流
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: f214e3a5230d6cf16b3bde5d89078160ed95f96f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519162"
---
# <a name="throttling"></a><span data-ttu-id="7102f-102">節流</span><span class="sxs-lookup"><span data-stu-id="7102f-102">Throttling</span></span>
<span data-ttu-id="7102f-103">節流範例會示範節流控制項的用法。</span><span class="sxs-lookup"><span data-stu-id="7102f-103">The Throttling sample demonstrates the use of throttling controls.</span></span> <span data-ttu-id="7102f-104">節流控制會限制同時呼叫、並行執行個體或工作階段的數目，以防止過度消耗資源。</span><span class="sxs-lookup"><span data-stu-id="7102f-104">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span> <span data-ttu-id="7102f-105">節流行為會指定於服務組態檔設定中。</span><span class="sxs-lookup"><span data-stu-id="7102f-105">Throttling behavior is specified in service configuration file settings.</span></span> <span data-ttu-id="7102f-106">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="7102f-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="7102f-107">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="7102f-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7102f-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="7102f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7102f-109">服務組態檔中指定節流控制項[ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="7102f-109">The service configuration file specifies throttling controls in a [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="7102f-110">當設定時，服務會將同時呼叫上限限制為 2，並行執行個體上限限制為 10。</span><span class="sxs-lookup"><span data-stu-id="7102f-110">As configured, the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span>  
  
 <span data-ttu-id="7102f-111">為了示範節流，我們在服務方法上定義了睡眠時間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7102f-111">In order to demonstrate throttling we define a sleep time on the service methods as follows:</span></span>  
  
```  
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 <span data-ttu-id="7102f-112">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="7102f-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7102f-113">Add 和 Subtract 方法會同時執行，而 Multiply 和 Divide 方法會同時執行，如此證明了無法同時執行兩個以上的方法，並因此示範了節流。</span><span class="sxs-lookup"><span data-stu-id="7102f-113">The Add and Subtract methods are executed concurrently and the Multiply and Divide methods are executed concurrently proving that not more than 2 methods can be executed concurrently thus demonstrating throttling.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7102f-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="7102f-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7102f-115">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7102f-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7102f-116">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="7102f-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7102f-117">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7102f-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7102f-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7102f-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7102f-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7102f-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7102f-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="7102f-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7102f-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7102f-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
  
## <a name="see-also"></a><span data-ttu-id="7102f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7102f-122">See Also</span></span>
