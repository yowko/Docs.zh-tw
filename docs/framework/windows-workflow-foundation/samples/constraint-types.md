---
title: Constraint 型別
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 53e5975017c3a27ede8ad07cd93f78f71df2d3e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517504"
---
# <a name="constraint-types"></a><span data-ttu-id="17c2f-102">Constraint 型別</span><span class="sxs-lookup"><span data-stu-id="17c2f-102">Constraint Types</span></span>
<span data-ttu-id="17c2f-103">這個範例示範兩種不同的方式將條件約束套用至工作流程：一個是從活動中 (建置)，另一個是從活動外部 (原則)。</span><span class="sxs-lookup"><span data-stu-id="17c2f-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="17c2f-104">在這個案例中，活動作者 (來自協力軟體廠商) 想要驗證兩個引數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="17c2f-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="17c2f-105">在此情況下，成本應該小於或等於價格。</span><span class="sxs-lookup"><span data-stu-id="17c2f-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="17c2f-106">這是一般驗證建置條件約束。</span><span class="sxs-lookup"><span data-stu-id="17c2f-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="17c2f-107">接著店主想要在這個泛型活動中加入驗證。</span><span class="sxs-lookup"><span data-stu-id="17c2f-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="17c2f-108">在此情況下，他希望大部分產品等於或小於 $9.99。</span><span class="sxs-lookup"><span data-stu-id="17c2f-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="17c2f-109">因此，他在 `CreateProduct` 活動上使用原則條件約束。</span><span class="sxs-lookup"><span data-stu-id="17c2f-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="17c2f-110">在範例中：</span><span class="sxs-lookup"><span data-stu-id="17c2f-110">In the sample:</span></span>  
  
 <span data-ttu-id="17c2f-111">活動作者 (建置) 必須：</span><span class="sxs-lookup"><span data-stu-id="17c2f-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="17c2f-112">建立條件約束 (`PriceGreaterThanCost`)。</span><span class="sxs-lookup"><span data-stu-id="17c2f-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="17c2f-113">這是所有驗證邏輯的所在位置。</span><span class="sxs-lookup"><span data-stu-id="17c2f-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="17c2f-114">覆寫 `System.Activities.CodeActivity.OnGetConstraints()`，並將條件約束 (`PriceGreaterThanCost`) 加入至條件約束 <xref:System.Collections.IList>。</span><span class="sxs-lookup"><span data-stu-id="17c2f-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="17c2f-115">工作流程作者 (原則) 必須：</span><span class="sxs-lookup"><span data-stu-id="17c2f-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="17c2f-116">建立具有要驗證之活動執行個體 (`CreateProduct`) 的工作流程。</span><span class="sxs-lookup"><span data-stu-id="17c2f-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="17c2f-117">建立條件約束 (`MaxPrice`)。</span><span class="sxs-lookup"><span data-stu-id="17c2f-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="17c2f-118">建立 <xref:System.Activities.Validation.ValidationSettings> 執行個體 (`validationSettings`)，並將條件約束 (`MaxPrice`) 加入至集合 `AdditionalConstraints`。</span><span class="sxs-lookup"><span data-stu-id="17c2f-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="17c2f-119">在這裡工作流程作者可以將原則條件約束加入至任何活動，例如序列或平行活動。</span><span class="sxs-lookup"><span data-stu-id="17c2f-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="17c2f-120">呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，傳回 <xref:System.Activities.Validation.ValidationResults> 物件的 <xref:System.Activities.Validation.ValidationError> 集合。</span><span class="sxs-lookup"><span data-stu-id="17c2f-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="17c2f-121">(選擇性) 列印 <xref:System.Activities.Validation.ValidationError> 物件。</span><span class="sxs-lookup"><span data-stu-id="17c2f-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="17c2f-122">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="17c2f-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="17c2f-123">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ConstraintTypes.sln 範例方案。</span><span class="sxs-lookup"><span data-stu-id="17c2f-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="17c2f-124">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="17c2f-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17c2f-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="17c2f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17c2f-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="17c2f-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="17c2f-127">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="17c2f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17c2f-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="17c2f-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`