---
title: "使用 FlowChart 及 Pick 組合的 StateMachine 案例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0fb0364310c8780dd41c5369e6b1851dee668d15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="7aead-102">使用 FlowChart 及 Pick 組合的 StateMachine 案例</span><span class="sxs-lookup"><span data-stu-id="7aead-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="7aead-103">這個範例示範如何實作一個使用 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Pick> 活動組合的簡單馬錶案例。</span><span class="sxs-lookup"><span data-stu-id="7aead-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="7aead-104">在 Pick 活動中使用 Receive 和 Send 以接聽馬錶事件。</span><span class="sxs-lookup"><span data-stu-id="7aead-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7aead-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7aead-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7aead-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7aead-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7aead-107">如果此目錄不存在，請移至 (下載頁面) 以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7aead-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7aead-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7aead-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="7aead-109">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="7aead-109">Sample Details</span></span>  
 <span data-ttu-id="7aead-110">下表列出這個範例中的專案。</span><span class="sxs-lookup"><span data-stu-id="7aead-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="7aead-111">專案名稱</span><span class="sxs-lookup"><span data-stu-id="7aead-111">Project Name</span></span>|<span data-ttu-id="7aead-112">描述</span><span class="sxs-lookup"><span data-stu-id="7aead-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="7aead-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="7aead-113">StopWatchService</span></span>|<span data-ttu-id="7aead-114">這個專案包含一個使用 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Pick> 活動組合之馬錶範例的狀態機器實作。</span><span class="sxs-lookup"><span data-stu-id="7aead-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="7aead-115"><xref:System.Activities.Statements.Pick> 活動的 <xref:System.Activities.Statements.PickBranch> 屬性中有 3 個 <xref:System.Activities.Statements.Pick.Branches%2A> 陳述式，會接聽 `GetStart`、`GetStop` 和 `GetOff` 事件。</span><span class="sxs-lookup"><span data-stu-id="7aead-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="7aead-116">根據傳入事件，每個分支的觸發程式會啟動，而且對應的 <xref:System.Activities.Statements.PickBranch.Action%2A> 會觸發。</span><span class="sxs-lookup"><span data-stu-id="7aead-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="7aead-117">在 <xref:System.Activities.Statements.PickBranch.Action%2A> 屬性中，<xref:System.Activities.Statements.Switch%601> 陳述式會評估狀態轉換是否為合法轉換，如果是的話，`currentState` 屬性會更新為轉換中狀態並傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="7aead-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="7aead-118">在 <xref:System.Activities.Statements.FlowDecision> 結束時 <xref:System.Activities.Statements.Flowchart> 活動會評估 `currentState` 屬性，以判斷狀態是否為末期。</span><span class="sxs-lookup"><span data-stu-id="7aead-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="7aead-119">如果是的話，工作流程會結束，否則控制權會循環回到 <xref:System.Activities.Statements.Pick> 活動的開頭，工作流程在此等候其他馬錶事件。</span><span class="sxs-lookup"><span data-stu-id="7aead-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="7aead-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="7aead-120">StopWatchClient</span></span>|<span data-ttu-id="7aead-121">這是簡單循序工作流程主控台應用程式，會傳送具有簡單 Send 或 Receive 活動組合的各種馬錶事件。</span><span class="sxs-lookup"><span data-stu-id="7aead-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7aead-122">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="7aead-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="7aead-123">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 StateMachineWithPick.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="7aead-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7aead-124">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="7aead-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7aead-125">開始從 StopWatchService.exe[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]身為系統管理員，以滑鼠右鍵按一下的.exe 檔案，並選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="7aead-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="7aead-126">巡覽至 StateMachineWithPick\CS\StopWatchService\bin\Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7aead-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="7aead-127">以滑鼠右鍵按一下 StopWatchService.exe 檔案，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="7aead-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="7aead-128">從 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中啟動 StopWatchClient 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="7aead-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="7aead-129">在**方案總管 中**，選取**StopWatchClient**專案，並以滑鼠右鍵按一下**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="7aead-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="7aead-130">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="7aead-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="7aead-131">切換回 StopWatchService.exe 的主控台視窗，以檢視狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="7aead-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7aead-132">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7aead-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7aead-133">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7aead-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7aead-134">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7aead-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7aead-135">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7aead-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="see-also"></a><span data-ttu-id="7aead-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7aead-136">See Also</span></span>
