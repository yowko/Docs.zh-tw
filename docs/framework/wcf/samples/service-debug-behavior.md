---
title: 服務偵錯行為
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: b87911426b6d4edf8a6f9b0172f4872fac7b9b6f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858882"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="83abe-102">服務偵錯行為</span><span class="sxs-lookup"><span data-stu-id="83abe-102">Service Debug Behavior</span></span>
<span data-ttu-id="83abe-103">這個範例會示範如何設定服務偵錯行為設定。</span><span class="sxs-lookup"><span data-stu-id="83abe-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="83abe-104">此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。</span><span class="sxs-lookup"><span data-stu-id="83abe-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="83abe-105">這個範例會在組態檔中明確地定義服務偵錯行為。</span><span class="sxs-lookup"><span data-stu-id="83abe-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="83abe-106">這個行為也可以透過程式碼，以命令方式定義。</span><span class="sxs-lookup"><span data-stu-id="83abe-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="83abe-107">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="83abe-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83abe-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="83abe-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="83abe-109">伺服器的 Web.config 檔會定義服務偵錯行為，以啟用說明網頁與例外狀況處理，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="83abe-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="83abe-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)是允許變更服務偵錯行為屬性的組態項目。</span><span class="sxs-lookup"><span data-stu-id="83abe-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="83abe-111">使用者可以修改這項行為以達到下列目的：</span><span class="sxs-lookup"><span data-stu-id="83abe-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="83abe-112">這可允許服務傳回應用程式碼擲回的任何例外狀況，即使例外狀況未使用 <xref:System.ServiceModel.FaultContractAttribute> 宣告。</span><span class="sxs-lookup"><span data-stu-id="83abe-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="83abe-113">將 `includeExceptionDetailInFaults` 設定為 `true`，便可達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="83abe-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="83abe-114">當在伺服器擲回非預期例外狀況的案例中偵錯時，這個設定非常有用。</span><span class="sxs-lookup"><span data-stu-id="83abe-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="83abe-115">在實際執行環境中開啟這項設定是不安全的。</span><span class="sxs-lookup"><span data-stu-id="83abe-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="83abe-116">未預期的伺服器例外狀況可能會包含某些不想要讓用戶端檢視的資訊，所以將 `includeExceptionDetailsInFaults` 設定為 `true` 可能會導致資訊洩漏。</span><span class="sxs-lookup"><span data-stu-id="83abe-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="83abe-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)也可讓使用者啟用或停用 [說明] 頁面。</span><span class="sxs-lookup"><span data-stu-id="83abe-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="83abe-118">每個服務都可以選擇公開一份說明網頁，其中包含的服務相關資訊可以包括取得服務之 WSDL 的端點。</span><span class="sxs-lookup"><span data-stu-id="83abe-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="83abe-119">將 `httpHelpPageEnabled` 設定為 `true`，便可啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="83abe-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="83abe-120">如此就可讓說明網頁傳回至要求服務基底位址的 GET 要求。</span><span class="sxs-lookup"><span data-stu-id="83abe-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="83abe-121">您可以藉由設定另一個 `httpHelpPageUrl` 屬性來變更這個位址。</span><span class="sxs-lookup"><span data-stu-id="83abe-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="83abe-122">如果改用 HTTPS 而非 HTTP，則可以保護其安全。</span><span class="sxs-lookup"><span data-stu-id="83abe-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="83abe-123">設定 `httpsHelpPageEnabled` 和 `httpsHelpPageUrl`，便可達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="83abe-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="83abe-124">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="83abe-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="83abe-125">前三項作業 (加法、減法以及乘法) 一定會成功。</span><span class="sxs-lookup"><span data-stu-id="83abe-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="83abe-126">最後一個作業 (「除法」) 會因為除數為零例外狀況而失敗。</span><span class="sxs-lookup"><span data-stu-id="83abe-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83abe-127">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="83abe-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="83abe-128">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="83abe-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="83abe-129">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="83abe-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="83abe-130">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="83abe-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83abe-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="83abe-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83abe-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="83abe-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83abe-133">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="83abe-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83abe-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="83abe-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a><span data-ttu-id="83abe-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83abe-135">See Also</span></span>
