---
title: "公司購買程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd5b8749ef2637dd1e9616257b5321ae7504dedd
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="corporate-purchase-process"></a><span data-ttu-id="7c11d-102">公司購買程序</span><span class="sxs-lookup"><span data-stu-id="7c11d-102">Corporate Purchase Process</span></span>
<span data-ttu-id="7c11d-103">這個範例示範如何建立一個具有自動最佳提案選取、非常基本的提案徵求書 (RFP) 架構採購程序。</span><span class="sxs-lookup"><span data-stu-id="7c11d-103">This sample shows how to create a very basic Request for Proposals (RFP) based purchase process with automatic best proposal selection.</span></span> <span data-ttu-id="7c11d-104">它結合 <xref:System.Activities.Statements.Parallel>、<xref:System.Activities.Statements.ParallelForEach%601> 和 <xref:System.Activities.Statements.ForEach%601>，以及自訂活動，建立代表此程序的工作流程。</span><span class="sxs-lookup"><span data-stu-id="7c11d-104">It combines <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, and <xref:System.Activities.Statements.ForEach%601> and a custom activity to create a workflow that represents the process.</span></span>  
  
 <span data-ttu-id="7c11d-105">這個範例包含 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 用戶端應用程式，可讓您以不同的參與者身分 (做為原始要求者或特定供應商) 與程序互動。</span><span class="sxs-lookup"><span data-stu-id="7c11d-105">This sample contains an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client application that allows interacting with the process as different participants (as the original requester or a particular vendor).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c11d-106">需求</span><span class="sxs-lookup"><span data-stu-id="7c11d-106">Requirements</span></span>  
  
-   [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="7c11d-107">.</span><span class="sxs-lookup"><span data-stu-id="7c11d-107">.</span></span>  
  
-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="7c11d-108">.</span><span class="sxs-lookup"><span data-stu-id="7c11d-108">.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7c11d-109">示範</span><span class="sxs-lookup"><span data-stu-id="7c11d-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="7c11d-110">自訂活動。</span><span class="sxs-lookup"><span data-stu-id="7c11d-110">Custom activities.</span></span>  
  
-   <span data-ttu-id="7c11d-111">活動撰寫。</span><span class="sxs-lookup"><span data-stu-id="7c11d-111">Composition of activities.</span></span>  
  
-   <span data-ttu-id="7c11d-112">書籤。</span><span class="sxs-lookup"><span data-stu-id="7c11d-112">Bookmarks.</span></span>  
  
-   <span data-ttu-id="7c11d-113">持續性。</span><span class="sxs-lookup"><span data-stu-id="7c11d-113">Persistence.</span></span>  
  
-   <span data-ttu-id="7c11d-114">結構描述化的持續性。</span><span class="sxs-lookup"><span data-stu-id="7c11d-114">Schematized persistence.</span></span>  
  
-   <span data-ttu-id="7c11d-115">追蹤。</span><span class="sxs-lookup"><span data-stu-id="7c11d-115">Tracing.</span></span>  
  
-   <span data-ttu-id="7c11d-116">追查。</span><span class="sxs-lookup"><span data-stu-id="7c11d-116">Tracking.</span></span>  
  
-   <span data-ttu-id="7c11d-117">在不同的用戶端 ([!INCLUDE[wf1](../../../../includes/wf1-md.md)] Web 應用程式和 WinForms 應用程式) 中裝載 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c11d-117">Hosting [!INCLUDE[wf1](../../../../includes/wf1-md.md)] in different clients ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web applications and WinForms applications).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c11d-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7c11d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c11d-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7c11d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c11d-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7c11d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c11d-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a><span data-ttu-id="7c11d-122">程序說明</span><span class="sxs-lookup"><span data-stu-id="7c11d-122">Description of the Process</span></span>  
 <span data-ttu-id="7c11d-123">這個範例示範如何實作 [!INCLUDE[wf](../../../../includes/wf-md.md)] 程式，從一般公司的供應商收集提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-123">This sample shows an implementation of a [!INCLUDE[wf](../../../../includes/wf-md.md)] program to gather proposals from vendors for a generic company.</span></span>  
  
1.  <span data-ttu-id="7c11d-124">X 公司的員工建立提案徵求書 (RFP)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-124">An employee of Company X creates a Request for Proposal (RFP).</span></span>  
  
    1.  <span data-ttu-id="7c11d-125">員工輸入 RFP 標題和描述。</span><span class="sxs-lookup"><span data-stu-id="7c11d-125">The employee types in the RFP title and description.</span></span>  
  
    2.  <span data-ttu-id="7c11d-126">員工選取數家供應商，希望邀請他們提交提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-126">The employee selects the vendors that he wants to invite to submit proposals.</span></span>  
  
2.  <span data-ttu-id="7c11d-127">員工提交提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-127">The employee submits the proposal.</span></span>  
  
    1.  <span data-ttu-id="7c11d-128">建立工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c11d-128">An instance of the workflow is created.</span></span>  
  
    2.  <span data-ttu-id="7c11d-129">工作流程等候所有供應商提交提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-129">The workflow is waiting for all vendors to submit their proposals.</span></span>  
  
3.  <span data-ttu-id="7c11d-130">收到所有提案之後，工作流程逐一查看所有收到的提案並選取最佳提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-130">After all proposals are received, the workflow iterates through all the received proposals and selects the best one.</span></span>  
  
    1.  <span data-ttu-id="7c11d-131">每個供應商都有評價 (這個範例將評價清單儲存在 VendorRepository.cs)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-131">Each vendor has a reputation (this sample stores the reputation list in VendorRepository.cs).</span></span>  
  
    2.  <span data-ttu-id="7c11d-132">提案的總值是由 (供應商輸入的值) * (供應商記錄評價) / 100 所決定。</span><span class="sxs-lookup"><span data-stu-id="7c11d-132">The total value of the proposal is determined by (The value typed in by the vendor) * (The vendor's recorded reputation) / 100.</span></span>  
  
4.  <span data-ttu-id="7c11d-133">原始要求者可以看到所有提交的提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-133">The original requester can see all the submitted proposals.</span></span> <span data-ttu-id="7c11d-134">在報表的特殊區段中呈現最佳提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-134">The best proposal is presented in a special section in the report.</span></span>  
  
## <a name="process-definition"></a><span data-ttu-id="7c11d-135">程序定義</span><span class="sxs-lookup"><span data-stu-id="7c11d-135">Process Definition</span></span>  
 <span data-ttu-id="7c11d-136">此範例的核心邏輯使用 <xref:System.Activities.Statements.ParallelForEach%601> 活動，等候每個供應商的提案 (使用可建立書籤的自訂活動)，而且將供應商提案註冊為 RFP (使用 <xref:System.Activities.Statements.InvokeMethod> 活動)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-136">The core logic of the sample uses a <xref:System.Activities.Statements.ParallelForEach%601> activity that waits for the offers from each vendor (using a custom activity that creates a bookmark), and registers the vendor proposal as an RFP (using an <xref:System.Activities.Statements.InvokeMethod> activity).</span></span>  
  
 <span data-ttu-id="7c11d-137">範例接著逐一查看儲存在 `RfpRepository` 中所有收到的提案，計算調整值 (使用 <xref:System.Activities.Statements.Assign> 活動和 <xref:System.Activities.Expressions> 活動)，如果調整值優於上一個最佳提案，則會將新值指派為最佳提案 (使用 <xref:System.Activities.Statements.If> 和 <xref:System.Activities.Statements.Assign> 活動)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-137">The sample then iterates through all of the received proposals stored in the `RfpRepository`, calculating the adjusted value (using an <xref:System.Activities.Statements.Assign> activity and <xref:System.Activities.Expressions> activities), and if the adjusted value is better than the previous best offer, assigns the new value as the best offer (using <xref:System.Activities.Statements.If> and <xref:System.Activities.Statements.Assign> activities).</span></span>  
  
## <a name="projects-in-this-sample"></a><span data-ttu-id="7c11d-138">這個範例中的專案</span><span class="sxs-lookup"><span data-stu-id="7c11d-138">Projects in this Sample</span></span>  
 <span data-ttu-id="7c11d-139">這個範例包含下列專案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-139">This sample contains the following projects.</span></span>  
  
|<span data-ttu-id="7c11d-140">Project</span><span class="sxs-lookup"><span data-stu-id="7c11d-140">Project</span></span>|<span data-ttu-id="7c11d-141">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c11d-142">通用</span><span class="sxs-lookup"><span data-stu-id="7c11d-142">Common</span></span>|<span data-ttu-id="7c11d-143">程序中使用的實體物件 (Request for Proposal、Vendor 和 Vendor Proposal)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-143">The entity objects used within the process (Request for Proposal, Vendor, and Vendor Proposal).</span></span>|  
|<span data-ttu-id="7c11d-144">WfDefinition</span><span class="sxs-lookup"><span data-stu-id="7c11d-144">WfDefinition</span></span>|<span data-ttu-id="7c11d-145">用戶端應用程式用來建立及使用採購程序工作流程執行個體之程序 ([!INCLUDE[wf1](../../../../includes/wf1-md.md)] 程式) 和主機 (`PurchaseProcessHost`) 的定義。</span><span class="sxs-lookup"><span data-stu-id="7c11d-145">The definition of the process (as a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) and host (`PurchaseProcessHost`) used by client applications for creating and using instances of the purchase process workflow.</span></span>|  
|<span data-ttu-id="7c11d-146">WebClient</span><span class="sxs-lookup"><span data-stu-id="7c11d-146">WebClient</span></span>|<span data-ttu-id="7c11d-147">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 用戶端應用程式，讓使用者建立及參與採購程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c11d-147">An [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client application that allows the users to create and participate in instances of the purchase process.</span></span> <span data-ttu-id="7c11d-148">它使用自訂建立的主機，以便與工作流程引擎互動。</span><span class="sxs-lookup"><span data-stu-id="7c11d-148">It uses a custom-created host to interact with the workflow engine.</span></span>|  
|<span data-ttu-id="7c11d-149">WinFormsClient</span><span class="sxs-lookup"><span data-stu-id="7c11d-149">WinFormsClient</span></span>|<span data-ttu-id="7c11d-150">Windows Form 用戶端應用程式，讓使用者建立及參與採購程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c11d-150">A Windows Forms client application that allows the users to create and participate in instances of the purchase process.</span></span> <span data-ttu-id="7c11d-151">它使用自訂建立的主機，以便與工作流程引擎互動。</span><span class="sxs-lookup"><span data-stu-id="7c11d-151">It uses a custom-created host to interact with the workflow engine.</span></span>|  
  
### <a name="wfdefinition"></a><span data-ttu-id="7c11d-152">WfDefinition</span><span class="sxs-lookup"><span data-stu-id="7c11d-152">WfDefinition</span></span>  
 <span data-ttu-id="7c11d-153">下表包含 WfDefinition 專案中最重要檔案的描述。</span><span class="sxs-lookup"><span data-stu-id="7c11d-153">The following table contains a description of the most important files in the WfDefinition project.</span></span>  
  
|<span data-ttu-id="7c11d-154">檔案</span><span class="sxs-lookup"><span data-stu-id="7c11d-154">File</span></span>|<span data-ttu-id="7c11d-155">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-155">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="7c11d-156">IPurchaseProcessHost.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-156">IPurchaseProcessHost.cs</span></span>|<span data-ttu-id="7c11d-157">工作流程主機的介面。</span><span class="sxs-lookup"><span data-stu-id="7c11d-157">Interface for the host of the workflow.</span></span>|  
|<span data-ttu-id="7c11d-158">PurchaseProcessHost.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-158">PurchaseProcessHost.cs</span></span>|<span data-ttu-id="7c11d-159">工作流程主機的實作。</span><span class="sxs-lookup"><span data-stu-id="7c11d-159">Implementation of a host for the workflow.</span></span> <span data-ttu-id="7c11d-160">此主機摘要工作流程執行階段的詳細資料，在所有用戶端應用程式中用來載入、執行 `PurchaseProcess` 工作流程執行個體，並與之互動。</span><span class="sxs-lookup"><span data-stu-id="7c11d-160">The host abstracts the details of the workflow runtime and is used in all the client applications to load, run, and interact with `PurchaseProcess` workflow instances.</span></span>|  
|<span data-ttu-id="7c11d-161">PurchaseProcessWorkflow.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-161">PurchaseProcessWorkflow.cs</span></span>|<span data-ttu-id="7c11d-162">包含採購程序工作流程定義的活動 (衍生自 <xref:System.Activities.Activity>)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-162">An activity that contains the definition of the Purchase Process workflow (derives from <xref:System.Activities.Activity>).</span></span><br /><br /> <span data-ttu-id="7c11d-163">衍生自 <xref:System.Activities.Activity> 的活動藉由組裝現有的自訂活動以及 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 活動程式庫中的活動來撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="7c11d-163">Activities that derive from <xref:System.Activities.Activity> compose functionality by assembling existing custom activities and activities from the [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] activity library.</span></span> <span data-ttu-id="7c11d-164">組裝這些活動是建立自訂功能最基本的方式。</span><span class="sxs-lookup"><span data-stu-id="7c11d-164">Assembling these activities is the most basic way to create custom functionality.</span></span>|  
|<span data-ttu-id="7c11d-165">WaitForVendorProposal.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-165">WaitForVendorProposal.cs</span></span>|<span data-ttu-id="7c11d-166">這個自訂活動衍生自 <xref:System.Activities.NativeActivity>，並且會建立具名書籤，供應商稍後在提交提案時必須繼續執行該書籤。</span><span class="sxs-lookup"><span data-stu-id="7c11d-166">This custom activity derives from <xref:System.Activities.NativeActivity> and creates a named bookmark that must be resumed later by a vendor when submitting the proposal.</span></span><br /><br /> <span data-ttu-id="7c11d-167">衍生自 <xref:System.Activities.NativeActivity> 的活動，就像衍生自 <xref:System.Activities.CodeActivity> 的活動一樣，會覆寫 <xref:System.Activities.NativeActivity.Execute%2A> 來建立命令式功能，但也可透過傳遞至 <xref:System.Activities.ActivityContext> 方法的 `Execute` 來存取工作流程執行階段的所有功能。</span><span class="sxs-lookup"><span data-stu-id="7c11d-167">Activities that derive from <xref:System.Activities.NativeActivity>, like those that derive from <xref:System.Activities.CodeActivity>, create imperative functionality by overriding <xref:System.Activities.NativeActivity.Execute%2A>, but also have access to all of the functionality of the workflow runtime through the <xref:System.Activities.ActivityContext> that gets passed into the `Execute` method.</span></span> <span data-ttu-id="7c11d-168">此內容支援排程與取消子活動、設定不保存區 (執行階段不保存工作流程資料的執行區段，例如在不可部分完成的交易中)，以及 <xref:System.Activities.Bookmark> 物件 (繼續暫止工作流程的控制代碼)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-168">This context has support for scheduling and canceling child activities, setting up no-persist zones (execution blocks during which the runtime does not persist the workflow’s data, such as within atomic transactions), and <xref:System.Activities.Bookmark> objects (handles for resuming paused workflows).</span></span>|  
|<span data-ttu-id="7c11d-169">TrackingParticipant.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-169">TrackingParticipant.cs</span></span>|<span data-ttu-id="7c11d-170">接收所有追蹤事件並將其儲存至文字檔的 <xref:System.Activities.Tracking.TrackingParticipant>。</span><span class="sxs-lookup"><span data-stu-id="7c11d-170">A <xref:System.Activities.Tracking.TrackingParticipant> that receives all tracking events and saves them to a text file.</span></span><br /><br /> <span data-ttu-id="7c11d-171">追蹤參與者會加入至工作流程執行個體做為延伸。</span><span class="sxs-lookup"><span data-stu-id="7c11d-171">Tracking participants are added to workflow instance as Extensions.</span></span>|  
|<span data-ttu-id="7c11d-172">XmlWorkflowInstanceStore.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-172">XmlWorkflowInstanceStore.cs</span></span>|<span data-ttu-id="7c11d-173">將工作流程應用程式儲存至 XML 檔案的自訂 <xref:System.Runtime.DurableInstancing.InstanceStore>。</span><span class="sxs-lookup"><span data-stu-id="7c11d-173">A custom <xref:System.Runtime.DurableInstancing.InstanceStore> that saves workflow applications to XML files.</span></span>|  
|<span data-ttu-id="7c11d-174">XmlPersistenceParticipant.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-174">XmlPersistenceParticipant.cs</span></span>|<span data-ttu-id="7c11d-175">將提案徵求書執行個體儲存至 XML 檔案的自訂 <xref:System.Activities.Persistence.PersistenceParticipant>。</span><span class="sxs-lookup"><span data-stu-id="7c11d-175">A custom <xref:System.Activities.Persistence.PersistenceParticipant> that saves an instance of request for proposal to an XML file.</span></span>|  
|<span data-ttu-id="7c11d-176">AsyncResult.cs / CompletedAsyncResult.cs</span><span class="sxs-lookup"><span data-stu-id="7c11d-176">AsyncResult.cs / CompletedAsyncResult.cs</span></span>|<span data-ttu-id="7c11d-177">在持續性元件中用來實作非同步模式的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="7c11d-177">Helper classes for implementing the asynchronous pattern in the persistence components.</span></span>|  
  
### <a name="common"></a><span data-ttu-id="7c11d-178">通用</span><span class="sxs-lookup"><span data-stu-id="7c11d-178">Common</span></span>  
 <span data-ttu-id="7c11d-179">下表包含通用專案中最重要類別的描述。</span><span class="sxs-lookup"><span data-stu-id="7c11d-179">The following table contains a description of the most important classes in the Common project.</span></span>  
  
|<span data-ttu-id="7c11d-180">類別</span><span class="sxs-lookup"><span data-stu-id="7c11d-180">Class</span></span>|<span data-ttu-id="7c11d-181">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-181">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c11d-182">Vendor</span><span class="sxs-lookup"><span data-stu-id="7c11d-182">Vendor</span></span>|<span data-ttu-id="7c11d-183">在提案徵求書中提交提案的供應商。</span><span class="sxs-lookup"><span data-stu-id="7c11d-183">A vendor that submits proposals in a Request for Proposals.</span></span>|  
|<span data-ttu-id="7c11d-184">RequestForProposal</span><span class="sxs-lookup"><span data-stu-id="7c11d-184">RequestForProposal</span></span>|<span data-ttu-id="7c11d-185">提案徵求書 (RFP) 是希望供應商對特定商品或服務提交提案的邀請。</span><span class="sxs-lookup"><span data-stu-id="7c11d-185">A request for proposals (RFP) is an invitation for vendors to submit proposals on a specific commodity or service.</span></span>|  
|<span data-ttu-id="7c11d-186">VendorProposal</span><span class="sxs-lookup"><span data-stu-id="7c11d-186">VendorProposal</span></span>|<span data-ttu-id="7c11d-187">供應商提交到具象 RFP 的提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-187">A proposal submitted by a vendor to a concrete RFP.</span></span>|  
|<span data-ttu-id="7c11d-188">VendorRepository</span><span class="sxs-lookup"><span data-stu-id="7c11d-188">VendorRepository</span></span>|<span data-ttu-id="7c11d-189">供應商的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="7c11d-189">The repository of Vendors.</span></span> <span data-ttu-id="7c11d-190">這個實作包含供應商執行個體的記憶體中集合以及公開這些執行個體的方法。</span><span class="sxs-lookup"><span data-stu-id="7c11d-190">This implementation contains an in-memory collection of instances of Vendor and methods for exposing those instances.</span></span>|  
|<span data-ttu-id="7c11d-191">RfpRepository</span><span class="sxs-lookup"><span data-stu-id="7c11d-191">RfpRepository</span></span>|<span data-ttu-id="7c11d-192">提案徵求書的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="7c11d-192">The repository of Requests for Proposals.</span></span> <span data-ttu-id="7c11d-193">這個實作包含使用 Linq to XML 查詢結構描述化的持續性所產生的提案徵求書 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-193">This implementation contains uses Linq to XML to query the XML file of Requests for Proposal generated by the schematized persistence.</span></span> <span data-ttu-id="7c11d-194">這個類別會實作[System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-194">This class implements [System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx).</span></span>|  
|<span data-ttu-id="7c11d-195">IOHelper</span><span class="sxs-lookup"><span data-stu-id="7c11d-195">IOHelper</span></span>|<span data-ttu-id="7c11d-196">這個類別處理所有 I/O 相關問題 (資料夾、路徑等等)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-196">This class handles all I/O-related issues (folders, paths, and so on.)</span></span>|  
  
### <a name="web-client"></a><span data-ttu-id="7c11d-197">Web 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c11d-197">Web Client</span></span>  
 <span data-ttu-id="7c11d-198">下表包含 Web 用戶端專案中最重要網頁的描述。</span><span class="sxs-lookup"><span data-stu-id="7c11d-198">The following table contains a description of the most important Web pages in the Web Client project.</span></span>  
  
|<span data-ttu-id="7c11d-199">檔案</span><span class="sxs-lookup"><span data-stu-id="7c11d-199">File</span></span>|<span data-ttu-id="7c11d-200">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-200">Description</span></span>|  
|-|-|  
|<span data-ttu-id="7c11d-201">CreateRfp.aspx</span><span class="sxs-lookup"><span data-stu-id="7c11d-201">CreateRfp.aspx</span></span>|<span data-ttu-id="7c11d-202">建立及提交新的提案徵求書。</span><span class="sxs-lookup"><span data-stu-id="7c11d-202">Creates and submits a new Request for Proposals.</span></span>|  
|<span data-ttu-id="7c11d-203">Default.aspx</span><span class="sxs-lookup"><span data-stu-id="7c11d-203">Default.aspx</span></span>|<span data-ttu-id="7c11d-204">顯示所有作用中和已完成的提案徵求書。</span><span class="sxs-lookup"><span data-stu-id="7c11d-204">Shows all active and completed Requests for Proposals.</span></span>|  
|<span data-ttu-id="7c11d-205">GetVendorProposal.aspx</span><span class="sxs-lookup"><span data-stu-id="7c11d-205">GetVendorProposal.aspx</span></span>|<span data-ttu-id="7c11d-206">在具象提案徵求書中取得供應商的提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-206">Gets a proposal from a vendor in a concrete Request for Proposals.</span></span> <span data-ttu-id="7c11d-207">此網頁僅由供應商使用。</span><span class="sxs-lookup"><span data-stu-id="7c11d-207">This page is used only by vendors.</span></span>|  
|<span data-ttu-id="7c11d-208">ShowRfp.aspx</span><span class="sxs-lookup"><span data-stu-id="7c11d-208">ShowRfp.aspx</span></span>|<span data-ttu-id="7c11d-209">顯示提案徵求書的所有相關資訊 (收到的提案、日期、值和其他資訊)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-209">Show all the information about a Request for Proposals (received proposals, dates, values, and other information).</span></span> <span data-ttu-id="7c11d-210">此網頁僅由提案徵求書建立者使用。</span><span class="sxs-lookup"><span data-stu-id="7c11d-210">This page is only used by the creator of the Request for Proposal.</span></span>|  
  
### <a name="winforms-client"></a><span data-ttu-id="7c11d-211">WinForms 用戶端</span><span class="sxs-lookup"><span data-stu-id="7c11d-211">WinForms Client</span></span>  
 <span data-ttu-id="7c11d-212">下表包含 Win Form 專案中最重要表單的描述。</span><span class="sxs-lookup"><span data-stu-id="7c11d-212">The following table contains a description of the most important forms in the Win Forms project.</span></span>  
  
|<span data-ttu-id="7c11d-213">表單</span><span class="sxs-lookup"><span data-stu-id="7c11d-213">Form</span></span>|<span data-ttu-id="7c11d-214">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-214">Description</span></span>|  
|-|-|  
|<span data-ttu-id="7c11d-215">NewRfp</span><span class="sxs-lookup"><span data-stu-id="7c11d-215">NewRfp</span></span>|<span data-ttu-id="7c11d-216">建立及提交新的提案徵求書。</span><span class="sxs-lookup"><span data-stu-id="7c11d-216">Creates and submits a new Request for Proposals.</span></span>|  
|<span data-ttu-id="7c11d-217">ShowProposals</span><span class="sxs-lookup"><span data-stu-id="7c11d-217">ShowProposals</span></span>|<span data-ttu-id="7c11d-218">顯示所有作用中和已完成的提案徵求書。</span><span class="sxs-lookup"><span data-stu-id="7c11d-218">Show all active and finished Requests for Proposals.</span></span> <span data-ttu-id="7c11d-219">**注意：**可能需要按一下**重新整理**UI，以查看在該螢幕上的變更之後您建立或修改提案徵求書, 中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c11d-219">**Note:**  You may need to click the **Refresh** button in the UI to see changes in that screen after you create or modify a Request for Proposal.</span></span>|  
|<span data-ttu-id="7c11d-220">SubmitProposal</span><span class="sxs-lookup"><span data-stu-id="7c11d-220">SubmitProposal</span></span>|<span data-ttu-id="7c11d-221">在具象提案徵求書中取得供應商的提案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-221">Get a proposal from a vendor in a concrete Request for Proposals.</span></span> <span data-ttu-id="7c11d-222">此視窗僅由供應商使用。</span><span class="sxs-lookup"><span data-stu-id="7c11d-222">This window is used only by vendors.</span></span>|  
|<span data-ttu-id="7c11d-223">ViewRfp</span><span class="sxs-lookup"><span data-stu-id="7c11d-223">ViewRfp</span></span>|<span data-ttu-id="7c11d-224">顯示提案徵求書的所有相關資訊 (收到的提案、日期、值和其他資訊)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-224">Show all the information about a Request for Proposals (received proposals, dates, values, and other information).</span></span> <span data-ttu-id="7c11d-225">此視窗僅由提案徵求書建立者使用。</span><span class="sxs-lookup"><span data-stu-id="7c11d-225">This window  is only used by the creator of the Request for Proposals.</span></span>|  
  
### <a name="persistence-files"></a><span data-ttu-id="7c11d-226">持續性檔案</span><span class="sxs-lookup"><span data-stu-id="7c11d-226">Persistence Files</span></span>  
 <span data-ttu-id="7c11d-227">下表顯示持續性提供者 (`XmlPersistenceProvider`) 所產生的檔案，這些檔案位於目前系統的暫存資料夾路徑 (使用 <xref:System.IO.Path.GetTempPath%2A>)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-227">The following table shows the files generated by the persistence provider (`XmlPersistenceProvider`) are located in the path of the current system's temporary folder (using <xref:System.IO.Path.GetTempPath%2A>).</span></span> <span data-ttu-id="7c11d-228">追蹤檔案是在目前執行路徑中建立的。</span><span class="sxs-lookup"><span data-stu-id="7c11d-228">The tracing file is created in the current execution path.</span></span>  
  
|<span data-ttu-id="7c11d-229">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="7c11d-229">File Name</span></span>|<span data-ttu-id="7c11d-230">描述</span><span class="sxs-lookup"><span data-stu-id="7c11d-230">Description</span></span>|<span data-ttu-id="7c11d-231">路徑</span><span class="sxs-lookup"><span data-stu-id="7c11d-231">Path</span></span>|  
|-|-|-|  
|<span data-ttu-id="7c11d-232">rfps.xml</span><span class="sxs-lookup"><span data-stu-id="7c11d-232">rfps.xml</span></span>|<span data-ttu-id="7c11d-233">具有所有作用中和已完成之提案徵求書的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-233">The XML file with all the active and finished Requests for Proposals.</span></span>|<xref:System.IO.Path.GetTempPath%2A>|  
|<span data-ttu-id="7c11d-234">[instanceid]</span><span class="sxs-lookup"><span data-stu-id="7c11d-234">[instanceid]</span></span>|<span data-ttu-id="7c11d-235">這個檔案包含工作流程執行個體的所有相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7c11d-235">This file contains all the information about a workflow instance.</span></span><br /><br /> <span data-ttu-id="7c11d-236">這個檔案是由結構描述化的持續性實作 (XmlPersistenceProvider 中的 PersistenceParticipant) 所產生的。</span><span class="sxs-lookup"><span data-stu-id="7c11d-236">This file is generated by the schematized persistence implementation (PersistenceParticipant in XmlPersistenceProvider).</span></span>|<xref:System.IO.Path.GetTempPath%2A>|  
|<span data-ttu-id="7c11d-237">[instanceId].tracking</span><span class="sxs-lookup"><span data-stu-id="7c11d-237">[instanceId].tracking</span></span>|<span data-ttu-id="7c11d-238">文字檔，其中有具象執行個體中發生的所有事件。</span><span class="sxs-lookup"><span data-stu-id="7c11d-238">A text file with all the events that occurred within a concrete instance.</span></span><br /><br /> <span data-ttu-id="7c11d-239">這個檔案是由 TrackingParticipant 所產生。</span><span class="sxs-lookup"><span data-stu-id="7c11d-239">This file is generated by TrackingParticipant.</span></span>|<xref:System.IO.Path.GetTempPath%2A>|  
|<span data-ttu-id="7c11d-240">PurchaseProcess.Tracing.TraceLog.txt</span><span class="sxs-lookup"><span data-stu-id="7c11d-240">PurchaseProcess.Tracing.TraceLog.txt</span></span>|<span data-ttu-id="7c11d-241">工作流程根據 App.config 或 Web.config 檔案中的組態參數所產生的追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-241">The tracing file generated by the workflow based on the configuration parameters in the App.config or Web.config files.</span></span>|<span data-ttu-id="7c11d-242">目前執行路徑</span><span class="sxs-lookup"><span data-stu-id="7c11d-242">Current execution path</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7c11d-243">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="7c11d-243">To use this sample</span></span>  
  
1.  <span data-ttu-id="7c11d-244">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 PurchaseProcess.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="7c11d-244">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the PurchaseProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7c11d-245">若要執行 Web 用戶端專案，請開啟**方案總管 中**以滑鼠右鍵按一下**Web 用戶端**專案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-245">To execute the Web Client project, open **Solution Explorer** and right-click the **Web Client** project.</span></span> <span data-ttu-id="7c11d-246">選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="7c11d-246">Select **Set as Startup Project**.</span></span>  
  
3.  <span data-ttu-id="7c11d-247">若要執行 WinForms 用戶端專案，請開啟**方案總管 中**以滑鼠右鍵按一下**WinForms 用戶端**專案。</span><span class="sxs-lookup"><span data-stu-id="7c11d-247">To execute the WinForms Client project, open **Solution Explorer** and right-click the **WinForms Client** project.</span></span> <span data-ttu-id="7c11d-248">選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="7c11d-248">Select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="7c11d-249">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="7c11d-249">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="7c11d-250">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="7c11d-250">To run the solution, press CTRL+F5.</span></span>  
  
### <a name="web-client-options"></a><span data-ttu-id="7c11d-251">Web 用戶端選項</span><span class="sxs-lookup"><span data-stu-id="7c11d-251">Web Client Options</span></span>  
  
-   <span data-ttu-id="7c11d-252">**建立新的 RFP**： 建立新提案徵求書 (RFP) 並且啟動採購程序工作流程。</span><span class="sxs-lookup"><span data-stu-id="7c11d-252">**Create a new RFP**: Creates a new Request for Proposals (RFP) and starts a Purchase Process workflow.</span></span>  
  
-   <span data-ttu-id="7c11d-253">**重新整理**： 重新整理的作用中 」 和 「 主要視窗中完成的 Rfp 清單。</span><span class="sxs-lookup"><span data-stu-id="7c11d-253">**Refresh**: Refreshes the list of Active and Finished RFPs in the main window.</span></span>  
  
-   <span data-ttu-id="7c11d-254">**檢視**： 顯示現有 RFP 的內容。</span><span class="sxs-lookup"><span data-stu-id="7c11d-254">**View**: Shows the content of an existing RFP.</span></span> <span data-ttu-id="7c11d-255">供應商可以提交提案 (如果受邀或 RFP 未完成)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-255">Vendors can submit their proposals (if invited or the RFP is not finished).</span></span>  
  
-   <span data-ttu-id="7c11d-256">View As： 使用者可以存取使用不同的身分識別選取所需的參與者中 RFP**以檢視**作用中 Rfp 方格中的下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="7c11d-256">View As: The user can access the RFP using different identities by selecting the desired participant in the **View as** combo box in the active RFPs grid.</span></span>  
  
### <a name="winforms-client-options"></a><span data-ttu-id="7c11d-257">WinForms 用戶端選項</span><span class="sxs-lookup"><span data-stu-id="7c11d-257">WinForms Client Options</span></span>  
  
-   <span data-ttu-id="7c11d-258">**Create RFP**： 建立新提案徵求書 (RFP) 並且啟動採購程序工作流程。</span><span class="sxs-lookup"><span data-stu-id="7c11d-258">**Create RFP**: Creates a new Request for Proposals (RFP) and starts a Purchase Process workflow.</span></span>  
  
-   <span data-ttu-id="7c11d-259">**重新整理**： 重新整理的作用中 」 和 「 主要視窗中完成的 Rfp 清單。</span><span class="sxs-lookup"><span data-stu-id="7c11d-259">**Refresh**: Refreshes the list of Active and Finished RFPs in the main window.</span></span>  
  
-   <span data-ttu-id="7c11d-260">**View RFP**： 顯示現有 RFP 的內容。</span><span class="sxs-lookup"><span data-stu-id="7c11d-260">**View RFP**: Shows the content of an existing RFP.</span></span> <span data-ttu-id="7c11d-261">供應商可以提交提案 (如果受邀或 RFP 未完成)。</span><span class="sxs-lookup"><span data-stu-id="7c11d-261">Vendors can submit their proposals (if invited or the RFP is not finished)</span></span>  
  
-   <span data-ttu-id="7c11d-262">**Connect As**： 使用者可以存取使用不同的身分識別選取所需的參與者中 RFP**以檢視**作用中 Rfp 方格中的下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="7c11d-262">**Connect As**: The user can access the RFP using different identities by selecting the desired participant in the **View as** combo box in the active RFPs grid.</span></span>