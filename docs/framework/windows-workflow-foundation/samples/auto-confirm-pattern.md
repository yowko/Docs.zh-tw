---
title: "自動確認模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3595e501341f64883ce2552f0a3c0850691f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="auto-confirm-pattern"></a><span data-ttu-id="74201-102">自動確認模式</span><span class="sxs-lookup"><span data-stu-id="74201-102">Auto-Confirm Pattern</span></span>
<span data-ttu-id="74201-103">這個範例包含三個狀況，其執行示範自訂 `AutoConfirmScope` 活動。</span><span class="sxs-lookup"><span data-stu-id="74201-103">This sample consists of three scenarios that run illustrating a custom `AutoConfirmScope` activity.</span></span> <span data-ttu-id="74201-104">第一個範例顯示四個可補償活動的序列成功執行，其中第二個和第三個可補償活動以巢狀方式置於 `AutoConfirmScope` 中。</span><span class="sxs-lookup"><span data-stu-id="74201-104">The first sample shows the successful execution of a sequence of four compensable activities where the second and third are nested in an `AutoConfirmScope`.</span></span> <span data-ttu-id="74201-105">第二個範例顯示相同序列，但在第四個 <xref:System.Activities.Statements.CompensableActivity> 執行後發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74201-105">The second sample shows the same sequence with an exception occurring after the execution of the fourth <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="74201-106">第三個狀況顯示相同序列，但在第二個  `AutoConfirmScope` 完成後於 <xref:System.Activities.Statements.CompensableActivity> 中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74201-106">The third scenario shows the same sequence with an exception occurring in the `AutoConfirmScope` after the second <xref:System.Activities.Statements.CompensableActivity> completes.</span></span>  
  
 <span data-ttu-id="74201-107">此範例示範在範圍成功完成時確認所有可補償子活動的自動確認模式。</span><span class="sxs-lookup"><span data-stu-id="74201-107">The sample demonstrates the auto-confirm pattern where all child compensable activities are confirmed upon successful completion of the scope.</span></span> <span data-ttu-id="74201-108">此模式定義所有可補償子活動的存留期間，因為它們不再補償或確認。</span><span class="sxs-lookup"><span data-stu-id="74201-108">This pattern defines the lifetime of all child compensable activities, as they can no longer be compensated or confirmed.</span></span>  
  
 <span data-ttu-id="74201-109">範圍是由 <xref:System.Activities.Statements.TryCatch> 組成，其中 <xref:System.Activities.Statements.TryCatch.Try%2A> 為內部 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="74201-109">The scope consists of a <xref:System.Activities.Statements.TryCatch> where the <xref:System.Activities.Statements.TryCatch.Try%2A> is an internal <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="74201-110">使用者指定的 `AutoConfirmScope` 主體是內部 <xref:System.Activities.Statements.CompensableActivity> 的主體。</span><span class="sxs-lookup"><span data-stu-id="74201-110">The user-specified body of the `AutoConfirmScope` is the body of the inner <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="74201-111">當這個內部 <xref:System.Activities.Statements.CompensableActivity> 完成時，它會產生 <xref:System.Activities.Statements.CompensationToken> 做為 out 引數。</span><span class="sxs-lookup"><span data-stu-id="74201-111">When this internal <xref:System.Activities.Statements.CompensableActivity> completes, it produces a <xref:System.Activities.Statements.CompensationToken> as an out-argument.</span></span> <span data-ttu-id="74201-112">`AutoConfirmScope` 使用 <xref:System.Activities.Statements.TryCatch.Finally%2A> 檢查語彙基元是否已產生，如果有的話，則會確認內部 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="74201-112">The `AutoConfirmScope` uses a <xref:System.Activities.Statements.TryCatch.Finally%2A> to check whether the token has been produced and if it has then it confirms the inner <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="74201-113">內部 <xref:System.Activities.Statements.CompensableActivity> 會針對其主體中可能存在的任何可補償活動叫用預設補償。</span><span class="sxs-lookup"><span data-stu-id="74201-113">The inner <xref:System.Activities.Statements.CompensableActivity> invokes the default compensation for any compensable activities that may exist in its body.</span></span>  
  
 <span data-ttu-id="74201-114">第一個狀況顯示工作流程的成功執行，並示範當工作流程完成且第一個和第四個可補償活動確認時，第二個和第三個可補償活動已確認。</span><span class="sxs-lookup"><span data-stu-id="74201-114">The first scenario shows successful execution of the workflow and demonstrates that the second and third compensable activities are already confirmed when the workflow completes and the first and fourth are confirmed.</span></span> <span data-ttu-id="74201-115">這產生三、二、四和一的確認順序。</span><span class="sxs-lookup"><span data-stu-id="74201-115">This produces a confirmation order of three, two, four, and one.</span></span>  
  
 <span data-ttu-id="74201-116">第二個狀況在四個可補償活動完成之後顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74201-116">The second scenario shows an exception after the four compensable activities have completed.</span></span> <span data-ttu-id="74201-117">因為可補償活動二和三已確認，它們不受影響，但一和四已補償。</span><span class="sxs-lookup"><span data-stu-id="74201-117">Because compensable activities two and three are already confirmed they are unaffected but one and four are compensated.</span></span> <span data-ttu-id="74201-118">這會產生確認三、確認二、補償四和補償一。</span><span class="sxs-lookup"><span data-stu-id="74201-118">This produces confirm three, confirm two, compensate four and compensate one.</span></span>  
  
 <span data-ttu-id="74201-119">最終狀況顯示 `AutoConfirmScope` 的不成功執行。</span><span class="sxs-lookup"><span data-stu-id="74201-119">The final scenario shows unsuccessful execution of the `AutoConfirmScope`.</span></span> <span data-ttu-id="74201-120">在這個狀況中，在第二個 <xref:System.Activities.Statements.CompensableActivity> 完成之後發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74201-120">In this scenario, an exception occurs after the completion of the second <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="74201-121">因為第三個和第四個可補償活動尚未執行，它們不受影響。</span><span class="sxs-lookup"><span data-stu-id="74201-121">Because the third and fourth compensable activities have not executed, they are unaffected.</span></span> <span data-ttu-id="74201-122">因為範圍未成功完成，所以第二個 <xref:System.Activities.Statements.CompensableActivity> 未確認。</span><span class="sxs-lookup"><span data-stu-id="74201-122">Because the scope did not complete successfully, the second <xref:System.Activities.Statements.CompensableActivity> does not get confirmed.</span></span> <span data-ttu-id="74201-123">這產生二和一的補償順序。</span><span class="sxs-lookup"><span data-stu-id="74201-123">This produces and compensation order of two then one.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="74201-124">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="74201-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="74201-125">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 AutoConfirmSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="74201-125">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the AutoConfirmSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="74201-126">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="74201-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="74201-127">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="74201-127">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74201-128">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="74201-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74201-129">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="74201-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74201-130">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="74201-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74201-131">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="74201-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`