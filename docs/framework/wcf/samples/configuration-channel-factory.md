---
title: "組態通道處理站"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a79a5c4997403f018ba34aea65e4c9fadab29443
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="10875-102">組態通道處理站</span><span class="sxs-lookup"><span data-stu-id="10875-102">Configuration Channel Factory</span></span>
<span data-ttu-id="10875-103">此範例涵蓋 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方法。</span><span class="sxs-lookup"><span data-stu-id="10875-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="10875-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 允許從中央管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="10875-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client configuration.</span></span> <span data-ttu-id="10875-105">如果在應用程式網域載入時間之後選取或變更組態，這可能也相當實用。</span><span class="sxs-lookup"><span data-stu-id="10875-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="10875-106">示範</span><span class="sxs-lookup"><span data-stu-id="10875-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="10875-107">討論</span><span class="sxs-lookup"><span data-stu-id="10875-107">Discussion</span></span>  
 <span data-ttu-id="10875-108">此範例示範如何使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 將特定組態檔加入至用戶端應用程式，而不必使用預設的應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="10875-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="10875-109">此範例包含二個專案。</span><span class="sxs-lookup"><span data-stu-id="10875-109">The sample consists of two projects.</span></span> <span data-ttu-id="10875-110">第一個專案是簡單服務，執行這個服務可回覆來自用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="10875-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="10875-111">第二個專案是用戶端應用程式，這個應用程式可以針對 Test.config 組態檔使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 建立兩個 <xref:System.Configuration.ExeConfigurationFileMap> 物件，並使用這兩個物件與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="10875-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="10875-112">兩個用戶端都會使用 Test.config 中指定的組態，與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="10875-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="10875-113">下列程式碼會將自訂組態檔加入至用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="10875-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10875-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="10875-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="10875-115">以系統管理員權限開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10875-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="10875-116">以滑鼠右鍵按一下 ConfigurationChannelFactory 方案 （2 個專案），然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="10875-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="10875-117">在**通用屬性**，選取**啟始專案**，然後按一下 **多個啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="10875-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="10875-118">移動**服務**與專案的清單中，開頭**動作 'Start'**，然後移動**用戶端**專案之後**服務**專案，也與**動作 'Start'**，因此**用戶端**之後執行專案時**服務**專案。</span><span class="sxs-lookup"><span data-stu-id="10875-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="10875-119">按一下**確定**，然後按下 F5 （或 CTRL + F5） 執行範例。</span><span class="sxs-lookup"><span data-stu-id="10875-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10875-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="10875-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10875-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="10875-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="10875-122">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="10875-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10875-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="10875-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
