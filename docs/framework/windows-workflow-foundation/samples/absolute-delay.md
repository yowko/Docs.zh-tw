---
title: "絕對延遲"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94eb9f401786ef05beaa51077ff4ddc170595752
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="absolute-delay"></a><span data-ttu-id="fc9ae-102">絕對延遲</span><span class="sxs-lookup"><span data-stu-id="fc9ae-102">Absolute Delay</span></span>
<span data-ttu-id="fc9ae-103">這個範例的主要案例是在工作流程應用程式中使用永久性計時器，以便延遲到指定的 <xref:System.DateTime> 為止。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="fc9ae-104">這項作業與使用內建的 <xref:System.Activities.Statements.Delay> 活動不同，因為這樣做只會允許您延遲給定的 <xref:System.TimeSpan> (或分鐘/秒數)。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="fc9ae-105">您可能會想要區別的一些實際案例包括：</span><span class="sxs-lookup"><span data-stu-id="fc9ae-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="fc9ae-106">您想要延遲傳送郵件 30 秒，確保沒有發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="fc9ae-107">您在加班時間內工作，而且想要將所有郵件都延遲到正常上班時間 (例如上午 8 點) 才傳送。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fc9ae-108">示範</span><span class="sxs-lookup"><span data-stu-id="fc9ae-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="fc9ae-109">用於實作絕對延遲的 <xref:System.Activities.Statements.DurableTimerExtension></span><span class="sxs-lookup"><span data-stu-id="fc9ae-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="fc9ae-110">使用永久性計時器的 <xref:System.Activities.WorkflowApplication> 設定持續性</span><span class="sxs-lookup"><span data-stu-id="fc9ae-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="fc9ae-111">透過 <xref:System.Activities.NativeActivity%601> 使用擴充點</span><span class="sxs-lookup"><span data-stu-id="fc9ae-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="fc9ae-112">在 SendEmail 活動中使用 <xref:System.Activities.CodeActivity%601></span><span class="sxs-lookup"><span data-stu-id="fc9ae-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="fc9ae-113">僅限 XAML 的工作流程</span><span class="sxs-lookup"><span data-stu-id="fc9ae-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="fc9ae-114">這個範例示範如何建立自訂活動，此活動會接受 <xref:System.DateTime> 並且使用永久性計時器來註冊延遲持續時間。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="fc9ae-115">使用永久性計時器時，您必須使用 <xref:System.Activities.NativeActivity> 來建立書籤，因為您必須利用計時器擴充註冊此書籤。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="fc9ae-116">在此範例中，當永久性計時器過期時，系統就會呼叫 `OnTimerExpired` 方法。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="fc9ae-117">請務必在 <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> 事件中加入計時器擴充，確保您會將這項資訊提供給執行階段。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="fc9ae-118">其他實作詳細資料就是，您必須實作邏輯，以便從 <xref:System.DateTime> 轉換成 <xref:System.TimeSpan>，因為永久性計時器只接受 <xref:System.DateTime>。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="fc9ae-119">請注意，這樣做會造成些微的精確度誤差。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc9ae-120">從 <xref:System.DateTime> 轉換成 <xref:System.TimeSpan> 時，會喪失些微的精確度。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="fc9ae-121">這個範例也會示範如何開啟 <xref:System.Activities.WorkflowApplication> 的持續性。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="fc9ae-122">在此特定範例中，我們將使用永久性計時器，以便在等候計時器過期的閒置時間內，將工作流程資料卸載至持續性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="fc9ae-123">這項實作也可用於其他持續性動作。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="fc9ae-124">此範例會示範如何使用 SQL Server 來設定持續性連接字串，以及如何建立執行個體存放區，以便保存工作流程執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="fc9ae-125">所提供的邏輯是有關如何在引發事件之後繼續工作流程，讓工作流程執行個體可執行。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="fc9ae-126">當您逐步執行這個範例時，您會看到內建延遲開始和完成的時間，接著導致系統傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an e-mail message to be sent.</span></span> <span data-ttu-id="fc9ae-127">之後，AbsoluteDelay 活動將中止直到指定的 <xref:System.DateTime> (或 0 秒，如果 <xref:System.DateTime> 已過期的話) 為止，接著便在過期時送出電子郵件。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="fc9ae-128">這將顯示內建 <xref:System.Activities.Statements.Delay> 功能與使用 AbsoluteDelay 活動的兩種不同使用案例。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc9ae-129">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="fc9ae-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fc9ae-130">請確定您已在電腦上安裝 SQL Server Express (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="fc9ae-131">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，執行 setup.cmd (位於 WF/Basic/Services/AbsoluteDelay/CS 中)，以便建立 AbsoluteDelaySampleDB 資料庫、建立持續性結構描述以及建立持續性邏輯。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="fc9ae-132">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="fc9ae-133">在 Delay 活動中指定 Duration。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="fc9ae-134">在 AbsoluteDelay 活動中指定 ExpirationTime。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="fc9ae-135">更新 SendMail 活動中的 SendMailTo、SendMailFrom、SendMailSubject、SendMailBody 和 SmtpHost 欄位。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc9ae-136">如果您沒有輸入有效的 SMTP 主機，應用程式將會擲回 SMTP 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="fc9ae-137">選取 建置方案**建置**，**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="fc9ae-138">執行方案，請按**F5**。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc9ae-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc9ae-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc9ae-141">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc9ae-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fc9ae-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
