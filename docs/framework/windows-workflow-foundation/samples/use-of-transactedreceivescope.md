---
title: "TransactedReceiveScope 的使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc43f04da0404c309c727aef93b74faec5047ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="28f2b-102">TransactedReceiveScope 的使用</span><span class="sxs-lookup"><span data-stu-id="28f2b-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="28f2b-103">這個範例示範如何將交易從用戶端流送至伺服器，方式是使用 <xref:System.Activities.Statements.TransactionScope> 在用戶端建立新交易，以及在伺服器上使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 接收有流動交易之訊息並設定交易存留期範圍。</span><span class="sxs-lookup"><span data-stu-id="28f2b-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="28f2b-104">這個範例包含兩個專案，可扮演用戶端和伺服器的角色。</span><span class="sxs-lookup"><span data-stu-id="28f2b-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="28f2b-105">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="28f2b-105">Client Application</span></span>  
 <span data-ttu-id="28f2b-106">用戶端應用程式會執行一個工作流程，此工作流程會列印分散式交易識別碼、傳送訊息給伺服器、讓交易流動、接收回應、再次列印分散式交易識別碼，然後完成。</span><span class="sxs-lookup"><span data-stu-id="28f2b-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="28f2b-107">當分散式交易識別碼最初列印時，它是空的 GUID 因為交易仍然在本機。</span><span class="sxs-lookup"><span data-stu-id="28f2b-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="28f2b-108">伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="28f2b-108">Server Application</span></span>  
 <span data-ttu-id="28f2b-109">伺服器專案很類似，但是工作流程會在 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中裝載，因為它必須接聽端點，取得來自用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="28f2b-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="28f2b-110">此工作流程會集中在 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，它會接收來自用戶端的流動交易、列印已傳送的訊息、列印分散式交易識別碼，然後回覆給用戶端。</span><span class="sxs-lookup"><span data-stu-id="28f2b-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="28f2b-111">分散式交易識別碼現在不是空的 GUID，而且如果可感知交易的活動已加入至 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 的主體，它會在流動交易之下執行。</span><span class="sxs-lookup"><span data-stu-id="28f2b-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="28f2b-112">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="28f2b-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="28f2b-113">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 TransactedReceiveScope.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="28f2b-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="28f2b-114">若要建置此方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="28f2b-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="28f2b-115">已成功建置，以滑鼠右鍵按一下方案，並選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="28f2b-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="28f2b-116">從對話方塊中，選取**多個啟始專案**，並確定這兩個專案的動作是**啟動**。</span><span class="sxs-lookup"><span data-stu-id="28f2b-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="28f2b-117">按 F5 或選取**開始偵錯**從**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="28f2b-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="28f2b-118">或者，您可以按 CTRL + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。</span><span class="sxs-lookup"><span data-stu-id="28f2b-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28f2b-119">啟動用戶端之前，伺服器必須在執行中。</span><span class="sxs-lookup"><span data-stu-id="28f2b-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="28f2b-120">裝載服務的主控台視窗中會顯示輸出，表示已啟動服務的時間。</span><span class="sxs-lookup"><span data-stu-id="28f2b-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28f2b-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="28f2b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28f2b-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="28f2b-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28f2b-123">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="28f2b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28f2b-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="28f2b-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`