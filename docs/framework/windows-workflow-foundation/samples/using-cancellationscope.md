---
title: "使用 CancellationScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae41255cea4621cbcd4050a5ebb04e662102bf77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-cancellationscope"></a><span data-ttu-id="997d0-102">使用 CancellationScope</span><span class="sxs-lookup"><span data-stu-id="997d0-102">Using CancellationScope</span></span>
<span data-ttu-id="997d0-103">這個範例示範如何使用 <xref:System.Activities.Statements.CancellationScope> 活動取消應用程式中的工作。</span><span class="sxs-lookup"><span data-stu-id="997d0-103">This sample demonstrates how to use the <xref:System.Activities.Statements.CancellationScope> activity to cancel work in an application.</span></span>  
  
 <span data-ttu-id="997d0-104">許多中介層元件和服務依賴已知的交易程式設計建構來處理取消作業。</span><span class="sxs-lookup"><span data-stu-id="997d0-104">Many middle tier components and services rely on the well-known programming construct of transactions to handle cancellation for them.</span></span>  <span data-ttu-id="997d0-105">不過，在許多情況下，必須取消交易中無法完成的工作。</span><span class="sxs-lookup"><span data-stu-id="997d0-105">However, there are many situations in which work that cannot be done in a transaction must be canceled.</span></span>  <span data-ttu-id="997d0-106">使用取消比使用交易更困難，因為必須取消的工作必須先加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="997d0-106">Using cancellation is more difficult than using transactions, because work that must be canceled must first be tracked.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="997d0-107"> 提供 <xref:System.Activities.Statements.CancellationScope> 活動，可協助您進行作業。</span><span class="sxs-lookup"><span data-stu-id="997d0-107"> helps you with this by providing a <xref:System.Activities.Statements.CancellationScope> activity.</span></span>  
  
 <span data-ttu-id="997d0-108">取消可以從活動中或從活動的父系中觸發。</span><span class="sxs-lookup"><span data-stu-id="997d0-108">Cancellation can be triggered either from within an activity or from the activity's parent.</span></span>  <span data-ttu-id="997d0-109">子活動是由父活動排程 (例如 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Parallel>、<xref:System.Activities.Statements.Flowchart> 或自訂複合活動)。</span><span class="sxs-lookup"><span data-stu-id="997d0-109">Child activities are scheduled by their parent activity (such as a <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, or a custom composite activity).</span></span>  <span data-ttu-id="997d0-110">父活動可以取消子活動，不計原因。</span><span class="sxs-lookup"><span data-stu-id="997d0-110">The parent activity can cancel child activities for any reason.</span></span>  <span data-ttu-id="997d0-111">例如，有三個子分支的 <xref:System.Activities.Statements.Parallel> 活動會在完成某個分支而且 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 運算式評估為 `true` 時取消其餘子分支。</span><span class="sxs-lookup"><span data-stu-id="997d0-111">For example, a <xref:System.Activities.Statements.Parallel> activity with three child branches will cancel the remaining child branches whenever it completes a branch and the <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> expression evaluates to `true`.</span></span> <span data-ttu-id="997d0-112">工作流程也可以由主應用程式呼叫 <xref:System.Activities.WorkflowApplication.Cancel%2A>，從外部取消。</span><span class="sxs-lookup"><span data-stu-id="997d0-112">The workflow can also be canceled externally by the host application by calling <xref:System.Activities.WorkflowApplication.Cancel%2A>.</span></span>  
  
 <span data-ttu-id="997d0-113">若要使用 <xref:System.Activities.Statements.CancellationScope> 活動，請將必須取消的工作放在 <xref:System.Activities.Statements.CancellationScope.Body%2A> 屬性中，並將取消後執行的工作放在 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="997d0-113">To use the <xref:System.Activities.Statements.CancellationScope> activity, put the work that needs to be canceled into the <xref:System.Activities.Statements.CancellationScope.Body%2A> property, and put the work that is performed after cancellation into the <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> property.</span></span>  
  
 <span data-ttu-id="997d0-114">這個範例示範如何從活動本身取消活動。</span><span class="sxs-lookup"><span data-stu-id="997d0-114">This sample demonstrates cancelling an activity from within the activity itself.</span></span>  
  
 <span data-ttu-id="997d0-115">此範例用來示範 <xref:System.Activities.Statements.CancellationScope> 活動的狀況是，客戶想要盡快購買到邁阿密的機票。</span><span class="sxs-lookup"><span data-stu-id="997d0-115">The scenario that the sample uses to demonstrate the <xref:System.Activities.Statements.CancellationScope> activity is a client wanting to buy a ticket to Miami as soon as possible.</span></span> <span data-ttu-id="997d0-116">有兩家旅行社想要做這筆生意。</span><span class="sxs-lookup"><span data-stu-id="997d0-116">There are two travel agencies that want the business.</span></span> <span data-ttu-id="997d0-117">此範例在 <xref:System.Activities.Statements.CancellationScope> 活動中使用兩個 <xref:System.Activities.Statements.Parallel>，以建立此商務邏輯的模型。</span><span class="sxs-lookup"><span data-stu-id="997d0-117">The sample uses two <xref:System.Activities.Statements.CancellationScope> within a <xref:System.Activities.Statements.Parallel> activity to model this business logic.</span></span> <span data-ttu-id="997d0-118"><xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 活動的 <xref:System.Activities.Statements.Parallel> 設為 `true`；因為在任何分支完成之後會檢查 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>，所以在第一個分支完成之後必須取消其餘分支。</span><span class="sxs-lookup"><span data-stu-id="997d0-118">The <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> of the <xref:System.Activities.Statements.Parallel> activity is set to `true`; since the <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> is checked after any branch completes, this will cause the remaining branch to be canceled after the first branch completes.</span></span> <span data-ttu-id="997d0-119">用戶端應用程式要求兩家旅行社購買機票，當第一家確認已買到機票時，應用程式會取消另一家的訂單。</span><span class="sxs-lookup"><span data-stu-id="997d0-119">The client application asks both agencies to buy the ticket, and when the first one confirms that the ticket has been bought, the application cancels the order at the other agency.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="997d0-120">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="997d0-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="997d0-121">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CancelationScopeXAML.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="997d0-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CancelationScopeXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="997d0-122">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="997d0-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="997d0-123">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="997d0-123">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="997d0-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="997d0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="997d0-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="997d0-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="997d0-126">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="997d0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="997d0-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="997d0-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`