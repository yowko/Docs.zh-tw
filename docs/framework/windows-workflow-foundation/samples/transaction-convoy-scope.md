---
title: 異動防護範圍
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: 4b053c15768a20ade4a469c9a40af797f49c268b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516561"
---
# <a name="transaction-convoy-scope"></a><span data-ttu-id="1169f-102">異動防護範圍</span><span class="sxs-lookup"><span data-stu-id="1169f-102">Transaction Convoy Scope</span></span>
<span data-ttu-id="1169f-103">這個範例示範如何建立 Parallel Convoy 訊息活動模式搭配 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，以建立多個作業可依任何順序同時在相同交易中發生的通訊協定模型。</span><span class="sxs-lookup"><span data-stu-id="1169f-103">This sample demonstrates how to create a Parallel Convoy messaging activity pattern in conjunction with a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to model a protocol where a number of operations can happen in any order all under the same transaction.</span></span> <span data-ttu-id="1169f-104">這個範例也示範 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 如何在沒有交易流向伺服器時自動建立新交易，因此用戶端不會利用任何交易。</span><span class="sxs-lookup"><span data-stu-id="1169f-104">This sample also demonstrates how a <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatically creates a new transaction when one is not flowed to the server, so the client does not make use of any transactions.</span></span>  
  
 <span data-ttu-id="1169f-105">這個範例包含兩個代表用戶端和伺服器的工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="1169f-105">The sample consists of two workflow projects that represent the client and server.</span></span> <span data-ttu-id="1169f-106">用戶端專案執行的工作流程一開始會先傳送訊息，以啟動載入伺服器工作流程，後者則會初始化相互關聯，並為其餘訊息活動啟動交易式範圍。</span><span class="sxs-lookup"><span data-stu-id="1169f-106">The client project runs a workflow that begins by sending a message to bootstrap the server workflow, which initializes a correlation and starts a transactional scope for the remainder of the messaging activities.</span></span> <span data-ttu-id="1169f-107">用戶端 <xref:System.Activities.Statements.Sequence> 活動包含初始 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 配對，接著是含有三個分支的 <xref:System.Activities.Statements.Parallel> 活動。</span><span class="sxs-lookup"><span data-stu-id="1169f-107">The client <xref:System.Activities.Statements.Sequence> activity contains an initial <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> pair and then a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="1169f-108">每個分支會傳送單向訊息給伺服器。</span><span class="sxs-lookup"><span data-stu-id="1169f-108">Each branch sends a one-way message to the server.</span></span> <span data-ttu-id="1169f-109"><xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 活動的 <xref:System.Activities.Statements.Parallel> 屬性設為 `false`，因此所有三個分支已完成。</span><span class="sxs-lookup"><span data-stu-id="1169f-109">The <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> property of the <xref:System.Activities.Statements.Parallel> activity is set to `false` so that all three branches complete.</span></span>  
  
 <span data-ttu-id="1169f-110">伺服器工作流程與用戶端工作流程類似，不同之處在於訊息活動導向通訊的伺服器端，而且包含在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動中，因此所有完成的工作都是在相同交易中執行。</span><span class="sxs-lookup"><span data-stu-id="1169f-110">The server workflow is similar to the client workflow except the messaging activities are oriented towards the server side of the communication and they are contained within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity so that all work done executes under the same transaction.</span></span> <span data-ttu-id="1169f-111">當伺服器接收第一個訊息時，會建立交易，而此交易會成為 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 主體範圍的環境交易，於是此範圍內的任何活動都可以存取此交易。</span><span class="sxs-lookup"><span data-stu-id="1169f-111">When the first message is received on the server, a transaction is created and is made ambient for the scope of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body so that any activity within this scope can access the transaction.</span></span> <span data-ttu-id="1169f-112">在此之後，所有接收活動都會平行執行。</span><span class="sxs-lookup"><span data-stu-id="1169f-112">After this, all receives execute in parallel.</span></span> <span data-ttu-id="1169f-113">所有接收活動只能執行一次，如平行活動的完成交易所描述。</span><span class="sxs-lookup"><span data-stu-id="1169f-113">All receives must execute exactly once as described by the completion condition on the parallel activity.</span></span> <span data-ttu-id="1169f-114"><xref:System.ServiceModel.Activities.TransactedReceiveScope> 主體結尾有隱含持續點，而且持續性作業也會在相同交易中執行。</span><span class="sxs-lookup"><span data-stu-id="1169f-114">An implicit persistence point exists at the end of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body and the persistence operation is also executed under the same transaction.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1169f-115">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="1169f-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="1169f-116">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ParallelConvoySample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="1169f-116">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ParallelConvoySample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1169f-117">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="1169f-117">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1169f-118">確認兩個專案都是設為起始專案。</span><span class="sxs-lookup"><span data-stu-id="1169f-118">Ensure both projects are set to start.</span></span>  
  
    1.  <span data-ttu-id="1169f-119">在**方案總管 中**，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="1169f-119">In **Solution Explorer**, right-click the solution and select **Set Startup Projects**.</span></span>  
  
    2.  <span data-ttu-id="1169f-120">選取**多個啟始專案**，請確定這兩個專案的動作設定為**啟動**。</span><span class="sxs-lookup"><span data-stu-id="1169f-120">Select **Multiple Startup Projects** and ensure the action for both projects is set to **Start**.</span></span>  
  
4.  <span data-ttu-id="1169f-121">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="1169f-121">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="1169f-122">伺服器會列印 `Server is running`，表示伺服器就緒。</span><span class="sxs-lookup"><span data-stu-id="1169f-122">The server prints `Server is running`, which indicates the server is ready.</span></span>  
  
     <span data-ttu-id="1169f-123">在用戶端主控台視窗中按任何鍵，以啟動範例。</span><span class="sxs-lookup"><span data-stu-id="1169f-123">Press any key in the client console window to start the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1169f-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1169f-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1169f-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1169f-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1169f-126">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="1169f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1169f-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1169f-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`