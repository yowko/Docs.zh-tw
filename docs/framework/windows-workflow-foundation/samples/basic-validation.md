---
title: "基本驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d388b3d6acad28e4ff952f72aa64a607d745f307
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="basic-validation"></a><span data-ttu-id="1163a-102">基本驗證</span><span class="sxs-lookup"><span data-stu-id="1163a-102">Basic Validation</span></span>
<span data-ttu-id="1163a-103">這個範例包含 `CreateProduct` 活動，會驗證其 `Cost` 引數小於或等於其 `Price` 引數。</span><span class="sxs-lookup"><span data-stu-id="1163a-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="1163a-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="1163a-104">Sample Details</span></span>  
 <span data-ttu-id="1163a-105">有兩個作者會使用驗證：建立活動驗證邏輯的活動作者，以及在特定工作流程上呼叫驗證服務的工作流程作者。</span><span class="sxs-lookup"><span data-stu-id="1163a-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="1163a-106">在這個案例中，活動作者想要強制每個活動執行個體的成本必須小於或等於價格。</span><span class="sxs-lookup"><span data-stu-id="1163a-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="1163a-107">活動作者 (在活動中) 必須：</span><span class="sxs-lookup"><span data-stu-id="1163a-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="1163a-108">建立條件約束 (`PriceGreaterThanCost`)。</span><span class="sxs-lookup"><span data-stu-id="1163a-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="1163a-109">這是所有驗證邏輯的所在位置。</span><span class="sxs-lookup"><span data-stu-id="1163a-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="1163a-110">覆寫 `System.Activities.CodeActivity.OnGetConstraints()`，並將條件約束 (`PriceGreaterThanCost`) 加入至條件約束 <xref:System.Collections.IList>。</span><span class="sxs-lookup"><span data-stu-id="1163a-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="1163a-111">工作流程作者 (主程式) 必須：</span><span class="sxs-lookup"><span data-stu-id="1163a-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="1163a-112">建立具有要驗證之活動執行個體 (`CreateProduct`) 的工作流程。</span><span class="sxs-lookup"><span data-stu-id="1163a-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="1163a-113">呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，傳回 <xref:System.Activities.Validation.ValidationResults> 的 <xref:System.Activities.Validation.ValidationError> 集合。</span><span class="sxs-lookup"><span data-stu-id="1163a-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="1163a-114">(選擇性) 列印 <xref:System.Activities.Validation.ValidationError> 物件。</span><span class="sxs-lookup"><span data-stu-id="1163a-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1163a-115">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="1163a-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1163a-116">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 BasicValidation.sln 範例方案。</span><span class="sxs-lookup"><span data-stu-id="1163a-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1163a-117">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="1163a-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1163a-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1163a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1163a-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1163a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1163a-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="1163a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1163a-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1163a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## <a name="see-also"></a><span data-ttu-id="1163a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1163a-122">See Also</span></span>
