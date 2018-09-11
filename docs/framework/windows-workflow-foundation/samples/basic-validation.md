---
title: 基本驗證
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264221"
---
# <a name="basic-validation"></a><span data-ttu-id="98004-102">基本驗證</span><span class="sxs-lookup"><span data-stu-id="98004-102">Basic Validation</span></span>
<span data-ttu-id="98004-103">這個範例包含 `CreateProduct` 活動，會驗證其 `Cost` 引數小於或等於其 `Price` 引數。</span><span class="sxs-lookup"><span data-stu-id="98004-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="98004-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="98004-104">Sample Details</span></span>  
 <span data-ttu-id="98004-105">有兩個作者會使用驗證：建立活動驗證邏輯的活動作者，以及在特定工作流程上呼叫驗證服務的工作流程作者。</span><span class="sxs-lookup"><span data-stu-id="98004-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="98004-106">在這個案例中，活動作者想要強制每個活動執行個體的成本必須小於或等於價格。</span><span class="sxs-lookup"><span data-stu-id="98004-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="98004-107">活動作者 (在活動中) 必須：</span><span class="sxs-lookup"><span data-stu-id="98004-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="98004-108">建立條件約束 (`PriceGreaterThanCost`)。</span><span class="sxs-lookup"><span data-stu-id="98004-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="98004-109">這是所有驗證邏輯的所在位置。</span><span class="sxs-lookup"><span data-stu-id="98004-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="98004-110">覆寫 `System.Activities.CodeActivity.OnGetConstraints()`，並將條件約束 (`PriceGreaterThanCost`) 加入至條件約束 <xref:System.Collections.IList>。</span><span class="sxs-lookup"><span data-stu-id="98004-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="98004-111">工作流程作者 (主程式) 必須：</span><span class="sxs-lookup"><span data-stu-id="98004-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="98004-112">建立具有要驗證之活動執行個體 (`CreateProduct`) 的工作流程。</span><span class="sxs-lookup"><span data-stu-id="98004-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="98004-113">呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，傳回 <xref:System.Activities.Validation.ValidationResults> 的 <xref:System.Activities.Validation.ValidationError> 集合。</span><span class="sxs-lookup"><span data-stu-id="98004-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="98004-114">(選擇性) 列印 <xref:System.Activities.Validation.ValidationError> 物件。</span><span class="sxs-lookup"><span data-stu-id="98004-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98004-115">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="98004-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="98004-116">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 BasicValidation.sln 範例方案。</span><span class="sxs-lookup"><span data-stu-id="98004-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="98004-117">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="98004-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98004-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="98004-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98004-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="98004-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98004-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="98004-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98004-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="98004-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`