---
title: 緩衝的接收
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9cd4dfcbfc9d417766615c624905f8bce2c10e54
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="buffered-receive"></a><span data-ttu-id="11183-102">緩衝的接收</span><span class="sxs-lookup"><span data-stu-id="11183-102">Buffered Receive</span></span>
<span data-ttu-id="11183-103">這個範例示範如何設定 [!INCLUDE[wf](../../../../includes/wf-md.md)] 中的緩衝接收功能。</span><span class="sxs-lookup"><span data-stu-id="11183-103">This sample demonstrates how to set up and configure the buffered receive feature in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="11183-104">緩衝接收可讓工作流程作者建立工作流程時不必擔心接收訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="11183-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="11183-105">緩衝接收功能會在本機緩衝處理訊息，並在工作流程準備要接收訊息時傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="11183-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="11183-106">示範</span><span class="sxs-lookup"><span data-stu-id="11183-106">Demonstrates</span></span>  
 <span data-ttu-id="11183-107">使用緩衝接收搭配訊息活動的失序訊息處理。</span><span class="sxs-lookup"><span data-stu-id="11183-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11183-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="11183-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11183-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="11183-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11183-110">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="11183-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11183-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="11183-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="11183-112">討論</span><span class="sxs-lookup"><span data-stu-id="11183-112">Discussion</span></span>  
 <span data-ttu-id="11183-113">在這個範例中，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務是使用 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 實作的，有數個 <xref:System.ServiceModel.Activities.Receive> 活動的序列。</span><span class="sxs-lookup"><span data-stu-id="11183-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="11183-114">這個工作流程是以簡單貸款核准程序為模型，其中工作流程預期接收三個通知，才會核准貸款。</span><span class="sxs-lookup"><span data-stu-id="11183-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="11183-115">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端應用程式以服務預期的相反方向傳送三個相互關聯的通知。</span><span class="sxs-lookup"><span data-stu-id="11183-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="11183-116">因為在服務開啟緩衝接收功能，所以每個失序訊息會在服務緩衝處理，並在工作流程準備要接收訊息時加以處理。</span><span class="sxs-lookup"><span data-stu-id="11183-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="11183-117">緩衝接收功能需要繫結的 <xref:System.ServiceModel.Activities.ReceiveContent> 支援，因此服務使用 <xref:System.ServiceModel.NetMsmqBinding>。</span><span class="sxs-lookup"><span data-stu-id="11183-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="11183-118">不需要繫結的特殊組態檔，因此會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="11183-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="11183-119">服務也會使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 來公開服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="11183-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="11183-120">同樣地，用戶端端點也是使用 <xref:System.ServiceModel.NetMsmqBinding> 設定的。</span><span class="sxs-lookup"><span data-stu-id="11183-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="11183-121">用戶端程式碼和組態使用所產生**加入服務參考**Visual Studio 功能。</span><span class="sxs-lookup"><span data-stu-id="11183-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="11183-122">下列範例是在 App.config 檔案中產生的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="11183-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="11183-123">本範例需要啟用下列 Windows 元件：</span><span class="sxs-lookup"><span data-stu-id="11183-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="11183-124"> 管理相容性、Metabase 和設定相容性</span><span class="sxs-lookup"><span data-stu-id="11183-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="11183-125">全球資訊網服務、應用程式開發功能和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="11183-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="11183-126">Microsoft Message Queues (MSMQ) 伺服器</span><span class="sxs-lookup"><span data-stu-id="11183-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="11183-127">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="11183-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="11183-128">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，輸入 `aspnet_regiis –I` 並按 ENTER，註冊 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="11183-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="11183-129">以系統管理員身分執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="11183-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="11183-130">開啟 LoanService.sln。</span><span class="sxs-lookup"><span data-stu-id="11183-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="11183-131">當系統詢問您想要建立 LoanService 專案的虛擬目錄，是否選取**是**。</span><span class="sxs-lookup"><span data-stu-id="11183-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="11183-132">若要設定服務佇列</span><span class="sxs-lookup"><span data-stu-id="11183-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="11183-133">按 F5 執行 LoanClient 應用程式，該應用程式會建立佇列以及啟動 Service1.xamlx 中定義的服務。</span><span class="sxs-lookup"><span data-stu-id="11183-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="11183-134">開啟**電腦管理**從命令提示字元執行 Compmgmt.msc 主控台。</span><span class="sxs-lookup"><span data-stu-id="11183-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="11183-135">在**電腦管理**主控台中，展開**服務**，**應用程式**，**訊息佇列**，**私用佇列**.</span><span class="sxs-lookup"><span data-stu-id="11183-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="11183-136">以滑鼠右鍵按一下 loanservice/service1.xamlx 佇列，並選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="11183-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="11183-137">選取**安全性**索引標籤，並加入**Everyone 接收訊息**，**查看訊息**和**傳送訊息**權限。</span><span class="sxs-lookup"><span data-stu-id="11183-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="11183-138">開啟 [[!INCLUDE[iis60](../../../../includes/iis60-md.md)] 管理員]。</span><span class="sxs-lookup"><span data-stu-id="11183-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="11183-139">瀏覽至**伺服器**，**網站**， **Default Web site**，**私人**， **LoanService**選取**進階的選項**</span><span class="sxs-lookup"><span data-stu-id="11183-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="11183-140">變更**啟用的通訊協定**是**http**， **net.msmq**。</span><span class="sxs-lookup"><span data-stu-id="11183-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="11183-141">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="11183-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="11183-142">瀏覽至http://localhost/private/loanservice/service1.xamlx以確保服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="11183-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="11183-143">按 F5 執行 LoanClient 應用程式。</span><span class="sxs-lookup"><span data-stu-id="11183-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="11183-144">一旦工作流程完成時，out.txt 檔案應該會儲存至 C:\Inbox，這個檔案包含訊息交換結果。</span><span class="sxs-lookup"><span data-stu-id="11183-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="11183-145">若要清除</span><span class="sxs-lookup"><span data-stu-id="11183-145">To clean up</span></span>  
  
1.  <span data-ttu-id="11183-146">開啟**電腦管理**從命令提示字元執行 Compmgmt.msc 主控台。</span><span class="sxs-lookup"><span data-stu-id="11183-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="11183-147">展開**服務**和**應用程式**，**訊息佇列**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="11183-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="11183-148">刪除 loanservice/service1.xamlx 佇列。</span><span class="sxs-lookup"><span data-stu-id="11183-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="11183-149">移除 C:\Inbox 目錄。</span><span class="sxs-lookup"><span data-stu-id="11183-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11183-150">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="11183-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11183-151">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="11183-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11183-152">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="11183-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11183-153">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="11183-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
