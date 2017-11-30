---
title: "外部活動驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f45d4ffc04b206db0dfefbdbbe683146e09c767f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="4c58e-102">外部活動驗證</span><span class="sxs-lookup"><span data-stu-id="4c58e-102">External Activity Validation</span></span>
<span data-ttu-id="4c58e-103">這個範例示範如何將驗證邏輯加入至不是您撰寫的內建活動。</span><span class="sxs-lookup"><span data-stu-id="4c58e-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="4c58e-104">驗證邏輯包含強制工作流程中的所有 <xref:System.Activities.Statements.If> 活動應設定 <xref:System.Activities.Statements.If.Then%2A> 屬性或 <xref:System.Activities.Statements.If.Else%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4c58e-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="4c58e-105">此外，驗證邏輯也包含檢查工作流程中的所有 <xref:System.Activities.Statements.Pick> 活動都有一個以上的分支，否則會產生警告。</span><span class="sxs-lookup"><span data-stu-id="4c58e-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4c58e-106">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="4c58e-106">Sample details</span></span>  
 <span data-ttu-id="4c58e-107">這個範例會建立工作流程，其中每個活動執行個體都要驗證：<xref:System.Activities.Statements.If> 活動和 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="4c58e-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="4c58e-108">每個驗證行為都會建立 <xref:System.Activities.Validation.Constraint>。</span><span class="sxs-lookup"><span data-stu-id="4c58e-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="4c58e-109">在這個範例中建立的條件約束是 `ConstraintError_IfShouldHaveThenOrElse` 和 `ConstraintWarning_PickHasOneBranch`。</span><span class="sxs-lookup"><span data-stu-id="4c58e-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="4c58e-110">接著，將這些條件約束加入至 `AdditionalConstraints` 執行個體的 <xref:System.Activities.Validation.ValidationSettings> 集合。</span><span class="sxs-lookup"><span data-stu-id="4c58e-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="4c58e-111">最後，呼叫 `static` 的 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A><xref:System.Activities.Validation.ActivityValidationServices> 方法，以驗證工作流程中的活動，並將驗證結果印出至主控台。</span><span class="sxs-lookup"><span data-stu-id="4c58e-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c58e-112">您可以將原則條件約束加入至任何活動。</span><span class="sxs-lookup"><span data-stu-id="4c58e-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="4c58e-113">例如，您可以將原則條件約束加入至 <xref:System.Activities.Statements.Sequence> 或 <xref:System.Activities.Statements.Parallel> 活動。</span><span class="sxs-lookup"><span data-stu-id="4c58e-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4c58e-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="4c58e-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="4c58e-115">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ExternalActivityValidation.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="4c58e-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="4c58e-116">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="4c58e-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4c58e-117">若要執行方案，請按下 Ctrl + F5。</span><span class="sxs-lookup"><span data-stu-id="4c58e-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c58e-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4c58e-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4c58e-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4c58e-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4c58e-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="4c58e-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4c58e-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4c58e-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`