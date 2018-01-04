---
title: "Windows 服務主機"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3634d5c14b0d0fcc0113296dec4843585625698d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-service-host"></a><span data-ttu-id="365c0-102">Windows 服務主機</span><span class="sxs-lookup"><span data-stu-id="365c0-102">Windows Service Host</span></span>
<span data-ttu-id="365c0-103">這個範例會示範裝載於受管理 Windows 服務中的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="365c0-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service hosted in a managed Windows Service.</span></span> <span data-ttu-id="365c0-104">Windows 服務控制使用中的 [服務] 小程式**控制台**和可以設定為在系統重新開機後自動啟動。</span><span class="sxs-lookup"><span data-stu-id="365c0-104">Windows Services are controlled using the Services applet in **Control Panel** and can be configured to start up automatically after a system reboot.</span></span> <span data-ttu-id="365c0-105">範例是由用戶端程式與 Windows 服務程式所組成。</span><span class="sxs-lookup"><span data-stu-id="365c0-105">The sample consists of a client program and an Windows Service program.</span></span> <span data-ttu-id="365c0-106">服務會實作為 .exe 程式並包含專屬的裝載程式碼。</span><span class="sxs-lookup"><span data-stu-id="365c0-106">The service is implemented as an .exe program and contains its own hosting code.</span></span> <span data-ttu-id="365c0-107">在其他裝載環境中，例如 Windows 處理序啟用服務 (WAS) 或 Internet Information Services (IIS)，就不需要撰寫裝載程式碼。</span><span class="sxs-lookup"><span data-stu-id="365c0-107">In other hosting environments, such as Windows Process Activation Services (WAS) or Internet Information Services (IIS), it is not necessary for you to write hosting code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="365c0-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="365c0-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="365c0-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="365c0-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="365c0-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="365c0-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="365c0-111">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="365c0-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="365c0-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="365c0-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 <span data-ttu-id="365c0-113">在這個服務完成建置後，它必須像任何其他 Windows 服務一樣使用 Installutil.exe 公用程式安裝。</span><span class="sxs-lookup"><span data-stu-id="365c0-113">After building this service, it must be installed with the Installutil.exe utility like any other Windows Service.</span></span> <span data-ttu-id="365c0-114">如果要變更服務，就必須先以 `installutil /u` 將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="365c0-114">If you are going to make changes to the service, you must first uninstall it with `installutil /u`.</span></span> <span data-ttu-id="365c0-115">這個範例中包含的 Setup.bat 和 Cleanup.bat 檔是用來安裝和啟動 Windows 服務，以及關閉和解除安裝 Windows 服務的命令。</span><span class="sxs-lookup"><span data-stu-id="365c0-115">The Setup.bat and Cleanup.bat files included in this sample are the commands to install and start up the Windows Service, and to shut down and uninstall the Windows Service.</span></span> <span data-ttu-id="365c0-116">只有在執行 Windows 服務的情況下，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務才會回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="365c0-116">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can only respond to clients if the Windows Service is running.</span></span> <span data-ttu-id="365c0-117">如果您使用從 [服務] 小程式停止 Windows 服務**控制台**並執行用戶端，<xref:System.ServiceModel.EndpointNotFoundException>用戶端嘗試存取服務時，就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="365c0-117">If you stop the Windows Service by using the Services applet from **Control Panel** and run the client, a <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="365c0-118">如果重新啟動 Windows 服務然後重新執行用戶端，就可成功進行通訊。</span><span class="sxs-lookup"><span data-stu-id="365c0-118">If you restart the Windows Service and rerun the client, communication succeeds.</span></span>  
  
 <span data-ttu-id="365c0-119">這段服務程式碼包含安裝程式類別、會實作 ICalculator 合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務實作類別，以及做為執行階段主機的 Windows 服務類別。</span><span class="sxs-lookup"><span data-stu-id="365c0-119">The service code includes an installer class, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service implementation class which implements the ICalculator contract, and a Windows Service class that acts as the run-time host.</span></span> <span data-ttu-id="365c0-120">繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別，會允許 Installutil.exe 工具將程式當做 NT 服務進行安裝。</span><span class="sxs-lookup"><span data-stu-id="365c0-120">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as an NT service by the Installutil.exe tool.</span></span> <span data-ttu-id="365c0-121">服務實作類別 `WcfCalculatorService` 是實作基本服務合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="365c0-121">The service implementation class, `WcfCalculatorService`, is an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements a basic service contract.</span></span> <span data-ttu-id="365c0-122">這個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務是裝載於稱為 `WindowsCalculatorService` 的 Windows 服務類別中。</span><span class="sxs-lookup"><span data-stu-id="365c0-122">This [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted inside a Windows Service class called `WindowsCalculatorService`.</span></span> <span data-ttu-id="365c0-123">為了限定為 Windows 服務，此類別會繼承自 <xref:System.ServiceProcess.ServiceBase>，並且實作 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 和 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法。</span><span class="sxs-lookup"><span data-stu-id="365c0-123">To qualify as a Windows Service, the class inherits from <xref:System.ServiceProcess.ServiceBase> and implements the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> and <xref:System.ServiceProcess.ServiceBase.OnStop> methods.</span></span> <span data-ttu-id="365c0-124">使用 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 時，會建立並開啟型別為 <xref:System.ServiceModel.ServiceHost> 的 `WcfCalculatorService` 物件。</span><span class="sxs-lookup"><span data-stu-id="365c0-124">In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, a <xref:System.ServiceModel.ServiceHost> object is created for the `WcfCalculatorService` type and opened.</span></span> <span data-ttu-id="365c0-125">使用 <xref:System.ServiceProcess.ServiceBase.OnStop> 時，會呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 物件的 <xref:System.ServiceModel.ServiceHost> 方法來關閉 ServiceHost。</span><span class="sxs-lookup"><span data-stu-id="365c0-125">In <xref:System.ServiceProcess.ServiceBase.OnStop>, the ServiceHost is closed by calling the <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> method of the <xref:System.ServiceModel.ServiceHost> object.</span></span> <span data-ttu-id="365c0-126">使用設定主機的基底位址[\<新增 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)項目子系的[ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)，這是子系[ \<主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)項目子系的[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)項目。</span><span class="sxs-lookup"><span data-stu-id="365c0-126">The host's base address is configured using the [\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, which is a child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), which is a child of the [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, which is a child of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element.</span></span>  
  
 <span data-ttu-id="365c0-127">定義端點使用的基底位址和[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="365c0-127">The endpoint that is defined uses the base address and a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="365c0-128">下列範例會示範設定基底位址，以及會公開 (Expose) CalculatorService 的端點。</span><span class="sxs-lookup"><span data-stu-id="365c0-128">The following sample shows the configuration of the base address as well as the endpoint that exposes the CalculatorService.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 <span data-ttu-id="365c0-129">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="365c0-129">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="365c0-130">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="365c0-130">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="365c0-131">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="365c0-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="365c0-132">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="365c0-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="365c0-133">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="365c0-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="365c0-134">在建置方案後，從提高權限的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行 Setup.bat，以便使用 Installutil.exe 工具來安裝 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="365c0-134">After the solution has been built, run Setup.bat from an elevated [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt to install the Windows service using the Installutil.exe tool.</span></span> <span data-ttu-id="365c0-135">此時該服務就會出現在 [服務] 中。</span><span class="sxs-lookup"><span data-stu-id="365c0-135">The service should appear in Services.</span></span>  
  
4.  <span data-ttu-id="365c0-136">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="365c0-136">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365c0-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="365c0-137">See Also</span></span>  
 [<span data-ttu-id="365c0-138">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="365c0-138">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
