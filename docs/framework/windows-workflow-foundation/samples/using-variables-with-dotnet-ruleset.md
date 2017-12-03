---
title: "搭配 .NET Framework 3.5 Ruleset 使用變數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5d0be8f8d88581e889ea2a659037f424a9a1c89
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="f377b-102">搭配 .NET Framework 3.5 Ruleset 使用變數</span><span class="sxs-lookup"><span data-stu-id="f377b-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="f377b-103">這個範例示範如何建立使用 <xref:System.Activities.Statements.Interop> 活動整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中使用原則和規則所撰寫自訂活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="f377b-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="f377b-104">工作流程會透過將變數繫結至自訂活動公開之相依性屬性的方式，將資料傳遞至自訂活動。</span><span class="sxs-lookup"><span data-stu-id="f377b-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="f377b-105">範例逐步解說</span><span class="sxs-lookup"><span data-stu-id="f377b-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="f377b-106">若要檢查 TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="f377b-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="f377b-107">使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開啟 [InteropWith35RuleSet.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f377b-107">Using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f377b-108">在工作流程設計工具中開啟 [TravelRuleSet.cs]。</span><span class="sxs-lookup"><span data-stu-id="f377b-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="f377b-109">包含 <xref:System.Workflow.Activities.PolicyActivity> 的自訂循序活動隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f377b-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="f377b-110">按兩下 [DiscountPolicy] 原則活動以檢查規則。</span><span class="sxs-lookup"><span data-stu-id="f377b-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="f377b-111">規則編輯器會出現並顯示規則。</span><span class="sxs-lookup"><span data-stu-id="f377b-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="f377b-112">以滑鼠右鍵按一下`DiscountPolicy`選取**檢視程式碼**選項，檢查程式碼旁置 C# 程式碼活動。</span><span class="sxs-lookup"><span data-stu-id="f377b-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="f377b-113">您會看見 `DiscountLevel` 的相依性屬性設定。</span><span class="sxs-lookup"><span data-stu-id="f377b-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="f377b-114">這相當於 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 中的引數。</span><span class="sxs-lookup"><span data-stu-id="f377b-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f377b-115">引數，請參閱[變數和引數](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="f377b-115"> arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="f377b-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="f377b-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="f377b-117">這是循序工作流程專案，該專案會使用 <xref:System.Activities.Statements.Interop> 活動整合 `TravelRuleLibrary` 專案中建立的自訂規則集。</span><span class="sxs-lookup"><span data-stu-id="f377b-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="f377b-118">變數會在 <xref:System.Activities.Statements.Sequence> 活動的最上層建立。</span><span class="sxs-lookup"><span data-stu-id="f377b-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="f377b-119"><xref:System.Activities.Statements.Interop> 活動會用來與 `TravelRuleSet` 活動整合。</span><span class="sxs-lookup"><span data-stu-id="f377b-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="f377b-120"><xref:System.Activities.Statements.Sequence> 上宣告的變數會用來繫結至相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="f377b-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="f377b-121">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="f377b-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="f377b-122">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [InteropWith35RuleSet.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f377b-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f377b-123">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="f377b-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f377b-124">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="f377b-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f377b-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f377b-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f377b-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f377b-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f377b-127">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f377b-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f377b-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f377b-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`