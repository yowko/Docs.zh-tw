---
title: 命令式自訂繫結
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44bedc3290d9c10078806ed63a8c5ddfe9754801
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="e478a-102">命令式自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e478a-102">Custom Binding Imperative</span></span>
<span data-ttu-id="e478a-103">此範例會示範如何撰寫命令式程式碼，以便在不使用組態檔或 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 產生之用戶端的情況下定義與使用自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="e478a-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] generated client.</span></span> <span data-ttu-id="e478a-104">這個範例會結合 HTTP 傳輸和可靠工作階段通道所提供的功能來建立可靠的 HTTP 架構繫結。</span><span class="sxs-lookup"><span data-stu-id="e478a-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="e478a-105">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="e478a-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e478a-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e478a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e478a-107">用戶端與服務端上都會建立包含兩種繫結項目 (可靠工作階段與 HTTP) 的自訂繫結：</span><span class="sxs-lookup"><span data-stu-id="e478a-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="e478a-108">在服務端上使用繫結的方式，是將端點新增至 ServiceHost：</span><span class="sxs-lookup"><span data-stu-id="e478a-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="e478a-109">在用戶端上，繫結會由 <xref:System.ServiceModel.ChannelFactory> 用來建立服務的通道：</span><span class="sxs-lookup"><span data-stu-id="e478a-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="e478a-110">接著，這個通道會用來與服務互動：</span><span class="sxs-lookup"><span data-stu-id="e478a-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="e478a-111">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e478a-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e478a-112">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="e478a-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e478a-113">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e478a-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e478a-114">確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e478a-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e478a-115">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e478a-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e478a-116">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e478a-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e478a-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e478a-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e478a-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e478a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e478a-119">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="e478a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e478a-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e478a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="e478a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e478a-121">See Also</span></span>  
 [<span data-ttu-id="e478a-122">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e478a-122">Custom Binding</span></span>](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08)
