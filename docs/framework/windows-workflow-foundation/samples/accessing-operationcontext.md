---
title: "存取 OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c0966299f27312deb188aec00abe9949dc27c2d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="94e88-102">存取 OperationContext</span><span class="sxs-lookup"><span data-stu-id="94e88-102">Accessing OperationContext</span></span>
<span data-ttu-id="94e88-103">這個範例會示範如何傳訊活動 (<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.Send>) 可以與自訂範圍活動用來存取<xref:System.ServiceModel.OperationContext.Current%2A>以及附加或擷取傳出或傳入訊息中的自訂訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="94e88-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="94e88-104">示範</span><span class="sxs-lookup"><span data-stu-id="94e88-104">Demonstrates</span></span>  
 <span data-ttu-id="94e88-105">訊息活動、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。</span><span class="sxs-lookup"><span data-stu-id="94e88-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="94e88-106">討論</span><span class="sxs-lookup"><span data-stu-id="94e88-106">Discussion</span></span>  
 <span data-ttu-id="94e88-107">這個範例示範如何在訊息活動中使用擴充點 (<xref:System.ServiceModel.Activities.ISendMessageCallback> 和 <xref:System.ServiceModel.Activities.IReceiveMessageCallback>)，以存取 <xref:System.ServiceModel.OperationContext.Current%2A>。</span><span class="sxs-lookup"><span data-stu-id="94e88-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="94e88-108">回呼是在工作流程執行階段中註冊成為 <xref:System.Activities.IExecutionProperty> 實作，而由訊息活動在完成時取用。</span><span class="sxs-lookup"><span data-stu-id="94e88-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="94e88-109">與該 <xref:System.Activities.IExecutionProperty> 實作位於相同範圍中的任何訊息活動都會受到影響。</span><span class="sxs-lookup"><span data-stu-id="94e88-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="94e88-110">尤其這個範例使用自訂範圍活動，強制執行回呼行為。</span><span class="sxs-lookup"><span data-stu-id="94e88-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="94e88-111">用戶端工作流程中會使用 <xref:System.ServiceModel.Activities.ISendMessageCallback>，包含工作流程的 <xref:System.Activities.WorkflowApplication.Id%2A> 做為傳出 <xref:System.ServiceModel.Channels.MessageHeader>。</span><span class="sxs-lookup"><span data-stu-id="94e88-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="94e88-112">接著服務會使用 <xref:System.ServiceModel.Activities.IReceiveMessageCallback> 取用此標頭，將標頭值印出至主控台。</span><span class="sxs-lookup"><span data-stu-id="94e88-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94e88-113">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="94e88-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94e88-114">這個範例使用 HTTP 端點公開工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="94e88-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="94e88-115">必須新增至執行此範例中，適當的 URL Acl (請參閱[設定 HTTP 和 HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)，以系統管理員身分執行 Visual Studio，或執行下列命令在提升權限的提示字元，加入適當的 Acl。</span><span class="sxs-lookup"><span data-stu-id="94e88-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="94e88-116">請確定您的網域和使用者名稱已用來取代。</span><span class="sxs-lookup"><span data-stu-id="94e88-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="94e88-117">一旦加入 URL ACL，請使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="94e88-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="94e88-118">建置方案。</span><span class="sxs-lookup"><span data-stu-id="94e88-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="94e88-119">設定多個啟始專案，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="94e88-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="94e88-120">新增**服務**和**用戶端**（依該順序） 做為多個啟始專案。</span><span class="sxs-lookup"><span data-stu-id="94e88-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="94e88-121">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="94e88-121">Run the application.</span></span> <span data-ttu-id="94e88-122">用戶端主控台會顯示執行兩次的工作流程，而 [服務] 視窗會顯示這些工作流程的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="94e88-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94e88-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="94e88-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94e88-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="94e88-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94e88-125">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="94e88-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94e88-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="94e88-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
