---
title: "隱藏異動範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9fb46dfee70cdcf136578a32709f3ceddddbeb81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="suppress-transaction-scope"></a><span data-ttu-id="9b9da-102">隱藏異動範圍</span><span class="sxs-lookup"><span data-stu-id="9b9da-102">Suppress Transaction Scope</span></span>
<span data-ttu-id="9b9da-103">此範例示範如何撰寫自訂 `SuppressTransactionScope` 活動，以隱藏環境執行階段交易 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="9b9da-103">The sample demonstrates how to author a custom `SuppressTransactionScope` activity to suppress the ambient run-time transaction, if present.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b9da-104">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9b9da-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9b9da-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9b9da-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9b9da-106">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="9b9da-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b9da-107">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9b9da-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a><span data-ttu-id="9b9da-108">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="9b9da-108">Sample Details</span></span>  
 <span data-ttu-id="9b9da-109">如果特定狀況不需要交易流程，此自訂活動可用來防止交易流出至另一個服務。</span><span class="sxs-lookup"><span data-stu-id="9b9da-109">The custom activity is useful to prevent a transaction from being flowed out to another service if transaction flow is undesirable for the particular scenario.</span></span> <span data-ttu-id="9b9da-110">工作流程執行階段的 <xref:System.Activities.NativeActivity> 類別中有隱藏環境交易的內建支援，但若要使用此支援，必須撰寫自訂 <xref:System.Activities.NativeActivity>，例如此範例所示範。</span><span class="sxs-lookup"><span data-stu-id="9b9da-110">The workflow runtime has built-in support for suppressing the ambient transaction in the <xref:System.Activities.NativeActivity> class, but to use this support it is necessary to author a custom <xref:System.Activities.NativeActivity> such as the one in this sample.</span></span>  
  
 <span data-ttu-id="9b9da-111">此狀況包含三個部分。</span><span class="sxs-lookup"><span data-stu-id="9b9da-111">The scenario consists of three parts.</span></span> <span data-ttu-id="9b9da-112">首先，<xref:System.Activities.Statements.TransactionScope> 建立可成為環境交易的執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="9b9da-112">First, a <xref:System.Activities.Statements.TransactionScope> creates a run-time transaction that becomes ambient.</span></span> <span data-ttu-id="9b9da-113">列印交易本機和分散式識別碼的自訂活動會予以驗證。</span><span class="sxs-lookup"><span data-stu-id="9b9da-113">This is verified by a custom activity that prints the local and distributed identifiers of the transaction.</span></span> <span data-ttu-id="9b9da-114">在第二部分開始之前，交易接著流向遠端服務。</span><span class="sxs-lookup"><span data-stu-id="9b9da-114">The transaction is then flowed to a remote service before beginning the second part.</span></span> <span data-ttu-id="9b9da-115">在第二部分期間，工作流程進入 `SuppressTransactionScope`，然後再度重複列印交易識別碼及流送交易的處理序。</span><span class="sxs-lookup"><span data-stu-id="9b9da-115">During the second part, the workflow enters a `SuppressTransactionScope` and again repeats the process of printing the transaction identifiers and flowing the transaction.</span></span> <span data-ttu-id="9b9da-116">不過，自訂活動找不到環境交易，而且流向服務的訊息不包含交易。</span><span class="sxs-lookup"><span data-stu-id="9b9da-116">However, the custom activity does not find an ambient transaction and the message flowed to the service does not contain the transaction.</span></span> <span data-ttu-id="9b9da-117">因此，服務會建立交易，表示用戶端和服務上列印的分散式識別碼不相符。</span><span class="sxs-lookup"><span data-stu-id="9b9da-117">As a result, the service creates a transaction, which means the distributed ID printed on the client and service do not match.</span></span> <span data-ttu-id="9b9da-118">在 `SuppressTransactionScope` 結束後發生最後一個部分，此時執行階段交易再度成為環境交易，另一個流向服務且其分散式識別碼符合第一個訊息之識別碼的訊息會予以驗證。</span><span class="sxs-lookup"><span data-stu-id="9b9da-118">The final part occurs after the `SuppressTransactionScope` exits and the run-time transaction again becomes ambient as verified by another message to the service with a distributed identifier that matches the identifier of the first message.</span></span>  
  
 <span data-ttu-id="9b9da-119">活動本身衍生自 <xref:System.Activities.NativeActivity>，因為它必須排定子活動以及加入執行屬性。</span><span class="sxs-lookup"><span data-stu-id="9b9da-119">The activity itself derives from <xref:System.Activities.NativeActivity> because it must schedule a child activity and add an execution property.</span></span> <span data-ttu-id="9b9da-120">`SuppressTransactionScope` 有 <xref:System.Activities.Variable> 類型的 <xref:System.Activities.RuntimeTransactionHandle>，因為控制代碼必須初始化，必須使用它，而不是 <xref:System.Activities.RuntimeTransactionHandle> 類型的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="9b9da-120">The `SuppressTransactionScope` has a <xref:System.Activities.Variable> of type <xref:System.Activities.RuntimeTransactionHandle>, which must be used rather than an instance field of type <xref:System.Activities.RuntimeTransactionHandle> because the handle must be initialized.</span></span> <span data-ttu-id="9b9da-121">`Variable<RuntimeTransactionHandle>` 由於僅供內部使用，因此會加入至活動的中繼資料做為實作變數。</span><span class="sxs-lookup"><span data-stu-id="9b9da-121">The `Variable<RuntimeTransactionHandle>` is added to the activity’s metadata as an implementation variable because it is only used internally.</span></span>  
  
 <span data-ttu-id="9b9da-122">當活動執行時，它會先檢查是否已指定主體，如果有的話，則會在 `SuppressTransaction` 上設定 <xref:System.Activities.RuntimeTransactionHandle> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b9da-122">When the activity is executed it first checks to see whether a body was specified and if so, sets the `SuppressTransaction` property on the <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="9b9da-123">一旦設定屬性，它會加入至執行屬性並成為環境屬性。</span><span class="sxs-lookup"><span data-stu-id="9b9da-123">Once the property is set, it is added to the execution properties and becomes ambient.</span></span> <span data-ttu-id="9b9da-124">這表示做為 `SuppressTransactionScope` 之子系的任何活動都可以看到此屬性，因此強制隱藏執行階段交易並導致巢狀 <xref:System.Activities.Statements.TransactionScope> 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9b9da-124">This means that any activity that is a child of the `SuppressTransactionScope` is able to see the property and therefore enforces the suppression of the run-time transaction and causes a nested <xref:System.Activities.Statements.TransactionScope> to throw an exception.</span></span> <span data-ttu-id="9b9da-125">一旦控制代碼加入至執行屬性，主體就會排定執行。</span><span class="sxs-lookup"><span data-stu-id="9b9da-125">Once the handle is added to the execution properties the body is scheduled to run.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9b9da-126">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="9b9da-126">To use this sample</span></span>  
  
1.  <span data-ttu-id="9b9da-127">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 SuppressTransactionScope.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="9b9da-127">Open the SuppressTransactionScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b9da-128">若要建置此方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="9b9da-128">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="9b9da-129">已成功建置，以滑鼠右鍵按一下方案，並選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="9b9da-129">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="9b9da-130">從對話方塊中，選取**多個啟始專案**，並確定這兩個專案的動作是**啟動**。</span><span class="sxs-lookup"><span data-stu-id="9b9da-130">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="9b9da-131">按 F5 或選取**開始偵錯**從**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="9b9da-131">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="9b9da-132">或者，您可以按 CTRL + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。</span><span class="sxs-lookup"><span data-stu-id="9b9da-132">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b9da-133">啟動用戶端之前，伺服器必須在執行中。</span><span class="sxs-lookup"><span data-stu-id="9b9da-133">The server must be running prior to starting the client.</span></span> <span data-ttu-id="9b9da-134">主控服務的主控台視窗中會顯示輸出，表示已啟動服務的時間。</span><span class="sxs-lookup"><span data-stu-id="9b9da-134">The output from the console window that hosts the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b9da-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9b9da-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9b9da-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9b9da-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9b9da-137">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="9b9da-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b9da-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9b9da-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`