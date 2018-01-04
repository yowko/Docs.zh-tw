---
title: NetNamedPipeBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1eab181ec63da5f0494ce5c4acabe6c6f868be15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="388bc-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="388bc-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="388bc-103">此範例示範 `netNamedPipeBinding` 繫結，這會在相同電腦上提供跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="388bc-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="388bc-104">具名通道不會跨電腦作業。</span><span class="sxs-lookup"><span data-stu-id="388bc-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="388bc-105">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)計算機服務。</span><span class="sxs-lookup"><span data-stu-id="388bc-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="388bc-106">在此範例中，服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="388bc-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="388bc-107">用戶端和服務都是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="388bc-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="388bc-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="388bc-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="388bc-109">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="388bc-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="388bc-110">中會指定繫結類型`binding`屬性[\<端點 >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目，如下列範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="388bc-110">The binding type is specified in the `binding` attribute of the[\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="388bc-111">前一個範例說明如何設定端點，以使用 `netNamedPipeBinding` 繫結搭配預設值。</span><span class="sxs-lookup"><span data-stu-id="388bc-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="388bc-112">如果您要設定 `netNamedPipeBinding` 繫結並變更其部分設定，則您必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="388bc-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="388bc-113">端點必須使用 `bindingConfiguration` 屬性，按照名稱參考繫結組態。</span><span class="sxs-lookup"><span data-stu-id="388bc-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="388bc-114">在此範例中，繫結組態會命名為 `Binding1`，並且具有下列定義：</span><span class="sxs-lookup"><span data-stu-id="388bc-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"   
             maxConnections="10"   
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="388bc-115">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="388bc-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="388bc-116">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="388bc-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="388bc-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="388bc-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="388bc-118">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="388bc-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="388bc-119">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="388bc-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="388bc-120">若要在單一電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="388bc-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="388bc-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="388bc-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="388bc-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="388bc-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="388bc-123">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="388bc-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="388bc-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="388bc-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
  
## <a name="see-also"></a><span data-ttu-id="388bc-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="388bc-125">See Also</span></span>
