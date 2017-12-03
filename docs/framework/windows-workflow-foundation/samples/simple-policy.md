---
title: "簡單原則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a2798c753e1fc526b2f95801d49108a2aba9e8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="simple-policy"></a><span data-ttu-id="36814-102">簡單原則</span><span class="sxs-lookup"><span data-stu-id="36814-102">Simple Policy</span></span>
<span data-ttu-id="36814-103">這個範例會示範如何在工作流程中使用 <xref:System.Workflow.Activities.PolicyActivity> 活動。</span><span class="sxs-lookup"><span data-stu-id="36814-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="36814-104">這個範例中的循序工作流程是使用 <xref:System.Workflow.Activities.PolicyActivity> 活動所建立的。</span><span class="sxs-lookup"><span data-stu-id="36814-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="36814-105">該工作流程會定義用來定義產品折扣工作流程的 `orderValue`、`customerType` 及 `discount` 欄位。</span><span class="sxs-lookup"><span data-stu-id="36814-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="36814-106">定義在規則檔案中的規則會根據 `orderValue` 和 `customerType` 來設定折扣值。</span><span class="sxs-lookup"><span data-stu-id="36814-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="36814-107">`orderValue` 和 `customerType` 會定義於 `SimplePolicyWorkflow` 類別定義，而且可以加以變更來改變行為。</span><span class="sxs-lookup"><span data-stu-id="36814-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="36814-108">結果產生的折扣將透過已定義於 <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> 類別中的 `SimplePolicyWorkflow` 事件處理常式來寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="36814-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="36814-109">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="36814-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="36814-110">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="36814-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="36814-111">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="36814-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="36814-112">按 CTRL+F5 執行方案，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="36814-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="36814-113">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="36814-113">To run the sample</span></span>  
  
-   <span data-ttu-id="36814-114">在 [SDK 命令提示字元] 視窗中，執行 SimplePolicy\bin\debug 資料夾 (若是範例的 Visual Basic 版本，則是 SimplePolicy\bin 資料夾) 中的 .exe 檔案，該資料夾位於此範例的主要資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="36814-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36814-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="36814-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="36814-116">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="36814-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="36814-117">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="36814-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="36814-118">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="36814-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="36814-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36814-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="36814-120">進階的原則</span><span class="sxs-lookup"><span data-stu-id="36814-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
