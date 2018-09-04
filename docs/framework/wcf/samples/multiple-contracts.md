---
title: 多個合約
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 040ab9b80e9567139ca4588e3ddf83b8f43f2d76
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565977"
---
# <a name="multiple-contracts"></a><span data-ttu-id="7a225-102">多個合約</span><span class="sxs-lookup"><span data-stu-id="7a225-102">Multiple Contracts</span></span>
<span data-ttu-id="7a225-103">多個合約範例會示範如何在服務上實作一個以上的合約，以及如何設定要與每個已實作合約進行通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="7a225-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="7a225-104">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7a225-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="7a225-105">此服務已修改成要定義兩個合約：`ICalculator` 以及 `ICalculatorSession` 合約。</span><span class="sxs-lookup"><span data-stu-id="7a225-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a225-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="7a225-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7a225-107">此服務類別會同時實作 `ICalculator` 和 `ICalculatorSession` 合約。</span><span class="sxs-lookup"><span data-stu-id="7a225-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="7a225-108">因為其中一個合約需要工作階段，所以服務會使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體模式來維護整個工作階段存留期間的狀態。</span><span class="sxs-lookup"><span data-stu-id="7a225-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="7a225-109">此服務組態已修改成定義兩個要公開各個合約的端點。</span><span class="sxs-lookup"><span data-stu-id="7a225-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="7a225-110">`ICalculator` 端點會以 `basicHttpBinding` 公開於基底位址。</span><span class="sxs-lookup"><span data-stu-id="7a225-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="7a225-111">`ICalculatorSession` 端點會以 `wsHttpBinding` 屬性設定為 `bindingConfiguration` 的 `BindingWithSession` 公開於基底位址/工作階段，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="7a225-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="7a225-112">產生的用戶端程式碼現在同時包含原始 `ICalculator` 合約與新 `ICalculatorSession` 合約的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="7a225-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="7a225-113">用戶端組態與程式碼已修改成可在適當的服務端點上與每個合約進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7a225-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="7a225-114">用戶端為主控台視窗應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="7a225-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="7a225-115">而服務是由網際網路資訊服務 (IIS) 裝載。</span><span class="sxs-lookup"><span data-stu-id="7a225-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="7a225-116">用戶端主控台視窗會顯示傳送至每個端點的作業，首先顯示基本端點，之後顯示安全端點。</span><span class="sxs-lookup"><span data-stu-id="7a225-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a225-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="7a225-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7a225-118">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7a225-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7a225-119">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="7a225-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7a225-120">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7a225-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7a225-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7a225-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a225-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7a225-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7a225-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="7a225-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a225-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7a225-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a><span data-ttu-id="7a225-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a225-125">See Also</span></span>
