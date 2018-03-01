---
title: "WS 可靠工作階段"
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
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c07130715b0416e7a8603b46a1c39c2f22dd7d2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ws-reliable-session"></a><span data-ttu-id="8f14a-102">WS 可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="8f14a-102">WS Reliable Session</span></span>
<span data-ttu-id="8f14a-103">這個範例會示範可靠工作階段的使用方式。</span><span class="sxs-lookup"><span data-stu-id="8f14a-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="8f14a-104">可靠工作階段會支援可信賴傳訊和工作階段。</span><span class="sxs-lookup"><span data-stu-id="8f14a-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="8f14a-105">可信賴傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。</span><span class="sxs-lookup"><span data-stu-id="8f14a-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="8f14a-106">工作階段會保持呼叫之間的用戶端狀態。</span><span class="sxs-lookup"><span data-stu-id="8f14a-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="8f14a-107">此範例會實作維持用戶端狀態的工作階段，並且指定依序傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="8f14a-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8f14a-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="8f14a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f14a-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="8f14a-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8f14a-110">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="8f14a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f14a-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="8f14a-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="8f14a-112">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="8f14a-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="8f14a-113">可靠工作階段的功能已在用戶端和服務的應用程式組態檔中啟用和設定。</span><span class="sxs-lookup"><span data-stu-id="8f14a-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="8f14a-114">在這個範例中，服務會由網際網路資訊服務 (IIS) 裝載，而用戶端是主控台應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="8f14a-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f14a-115">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="8f14a-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8f14a-116">這個範例會使用 `wsHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="8f14a-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="8f14a-117">用戶端和服務的組態檔中都會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="8f14a-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="8f14a-118">在端點項目的 `binding` 屬性中會指定繫結類型，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="8f14a-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="8f14a-119">端點包含參考名為 "Binding1." 之繫結組態的 `bindingConfiguration` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8f14a-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="8f14a-120">繫結組態會啟用可靠工作階段設定`enabled`屬性[ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)至`true`。</span><span class="sxs-lookup"><span data-stu-id="8f14a-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="8f14a-121">已排序工作階段之傳遞保證的控制方式，是將已排序的屬性設定為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="8f14a-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="8f14a-122">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8f14a-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="8f14a-123">服務實作類別會將 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體實作成維護每個用戶端的不同類別執行個體，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8f14a-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 <span data-ttu-id="8f14a-124">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="8f14a-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8f14a-125">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="8f14a-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f14a-126">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="8f14a-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8f14a-127">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="8f14a-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="8f14a-128">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8f14a-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="8f14a-129">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="8f14a-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="8f14a-130">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8f14a-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f14a-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f14a-131">See Also</span></span>
