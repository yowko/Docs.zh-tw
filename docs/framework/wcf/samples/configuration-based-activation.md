---
title: "以組態為基礎的啟用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc39a282cbb12b014c0749b3eb807f3248fca16e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation"></a><span data-ttu-id="21ad3-102">以組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="21ad3-102">Configuration-Based Activation</span></span>
<span data-ttu-id="21ad3-103">此範例示範如何在不需要 .svc 檔案的情況下啟動 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="21ad3-103">This sample demonstrates how to activate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21ad3-104">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="21ad3-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="21ad3-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="21ad3-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21ad3-106">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="21ad3-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21ad3-107">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="21ad3-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="21ad3-108">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="21ad3-108">Sample Details</span></span>  
 <span data-ttu-id="21ad3-109">在這個範例中，用戶端是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的測試用戶端，而服務是裝載在 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="21ad3-109">In this sample, the client is the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21ad3-110">此範例的安裝與建立指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="21ad3-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="21ad3-111">在不需要 .svc 檔案的情況下啟動服務</span><span class="sxs-lookup"><span data-stu-id="21ad3-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="21ad3-112">在 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中，啟動服務需要 .svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="21ad3-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="21ad3-113">這會造成額外的管理負荷，因為需要額外的檔案才能與應用程式一起進行部署和維護。</span><span class="sxs-lookup"><span data-stu-id="21ad3-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="21ad3-114">使用 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 版時，可以使用應用程式組態檔設定啟動元件。</span><span class="sxs-lookup"><span data-stu-id="21ad3-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="21ad3-115"> 在應用程式組態檔的 <xref:System.ServiceModel.Configuration.ServiceActivationElement> 中導入新的組態項目 (<xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>)。</span><span class="sxs-lookup"><span data-stu-id="21ad3-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="21ad3-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> 集合會接受一組要啟動的服務，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="21ad3-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="21ad3-117">結果是，此組態看起來非常類似 .svc 檔案的組態。</span><span class="sxs-lookup"><span data-stu-id="21ad3-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="21ad3-118">所導入的其他屬性為提供服務位址的 `relativeAddress`。</span><span class="sxs-lookup"><span data-stu-id="21ad3-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="21ad3-119">相對位址也就是服務的虛擬路徑。</span><span class="sxs-lookup"><span data-stu-id="21ad3-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="21ad3-120">主機會從 `virtualPath` 位置擷取檔案的 Web.config 檔 (如果存在)，否則，主機會以遞迴方搜尋其上層資料夾。</span><span class="sxs-lookup"><span data-stu-id="21ad3-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21ad3-121">此範例需要裝載在 IIS 中才能運作。</span><span class="sxs-lookup"><span data-stu-id="21ad3-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="21ad3-122">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="21ad3-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="21ad3-123">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Service.csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="21ad3-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="21ad3-124">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="21ad3-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="21ad3-125">執行 WCFTestClient.exe 來測試服務。</span><span class="sxs-lookup"><span data-stu-id="21ad3-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="21ad3-126">使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 巡覽至 %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21ad3-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="21ad3-127">執行 WcfTestClient.exe。</span><span class="sxs-lookup"><span data-stu-id="21ad3-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="21ad3-128">設定服務的 MEX 位址。</span><span class="sxs-lookup"><span data-stu-id="21ad3-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="21ad3-129">按下 CTRL+SHIFT+A 來設定服務位址。</span><span class="sxs-lookup"><span data-stu-id="21ad3-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="21ad3-130">將位址設定為 http://localhost/ServiceModelSamples/Calculator.svc。</span><span class="sxs-lookup"><span data-stu-id="21ad3-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="21ad3-131">執行 `Add` 作業。</span><span class="sxs-lookup"><span data-stu-id="21ad3-131">Perform the `Add` operation.</span></span> <span data-ttu-id="21ad3-132">將 `n1` 參數的值設定為 10，並將 `n2` 參數的值設定為 15。</span><span class="sxs-lookup"><span data-stu-id="21ad3-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="21ad3-133">按**叫用**。</span><span class="sxs-lookup"><span data-stu-id="21ad3-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="21ad3-134">預期的結果為 25。</span><span class="sxs-lookup"><span data-stu-id="21ad3-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21ad3-135">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="21ad3-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="21ad3-136">確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="21ad3-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="21ad3-137">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="21ad3-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="21ad3-138">在建立方案後，執行 Setup.bat 以便在 IIS 中安裝 ServiceModelSamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="21ad3-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="21ad3-139">ServiceModelSamples 目錄現在應該會顯示為 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="21ad3-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="21ad3-140">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="21ad3-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ad3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ad3-141">See Also</span></span>  
 [<span data-ttu-id="21ad3-142">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="21ad3-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
