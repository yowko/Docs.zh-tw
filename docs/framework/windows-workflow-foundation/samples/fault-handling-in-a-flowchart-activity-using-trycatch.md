---
title: 使用 TryCatch 錯誤處理流程圖活動
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: df3d93087744ce0fba597f5c9f1d2da4b71a50dd
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779851"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="211d4-102">使用 TryCatch 錯誤處理流程圖活動</span><span class="sxs-lookup"><span data-stu-id="211d4-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="211d4-103">這個範例示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="211d4-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

 <span data-ttu-id="211d4-104">在這個範例中，促銷碼和小孩人數會當做變數傳遞至 <xref:System.Activities.Statements.Flowchart> 活動，根據對應於促銷碼的公式來計算折扣。</span><span class="sxs-lookup"><span data-stu-id="211d4-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="211d4-105">此範例包含命令式程式碼和工作流程設計工具的範例版本。</span><span class="sxs-lookup"><span data-stu-id="211d4-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

 <span data-ttu-id="211d4-106">下表詳細說明 `CreateFlowchartWithFaults` 活動的變數。</span><span class="sxs-lookup"><span data-stu-id="211d4-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="211d4-107">參數</span><span class="sxs-lookup"><span data-stu-id="211d4-107">Parameters</span></span>|<span data-ttu-id="211d4-108">描述</span><span class="sxs-lookup"><span data-stu-id="211d4-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="211d4-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="211d4-109">promoCode</span></span>|<span data-ttu-id="211d4-110">促銷碼。</span><span class="sxs-lookup"><span data-stu-id="211d4-110">The promotion code.</span></span> <span data-ttu-id="211d4-111">類型：String</span><span class="sxs-lookup"><span data-stu-id="211d4-111">Type: String</span></span><br /><br /> <span data-ttu-id="211d4-112">可能的值，說明放在括號中：</span><span class="sxs-lookup"><span data-stu-id="211d4-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="211d4-113">-單一 （單一）</span><span class="sxs-lookup"><span data-stu-id="211d4-113">-   Single (Single)</span></span><br /><span data-ttu-id="211d4-114">-MNK （已婚，沒有小孩）。</span><span class="sxs-lookup"><span data-stu-id="211d4-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="211d4-115">-MWK （已婚，有小孩）</span><span class="sxs-lookup"><span data-stu-id="211d4-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="211d4-116">numKids</span><span class="sxs-lookup"><span data-stu-id="211d4-116">numKids</span></span>|<span data-ttu-id="211d4-117">小孩人數。</span><span class="sxs-lookup"><span data-stu-id="211d4-117">The number of children.</span></span> <span data-ttu-id="211d4-118">類型：int</span><span class="sxs-lookup"><span data-stu-id="211d4-118">Type: int</span></span>|

 <span data-ttu-id="211d4-119">`CreateFlowchartWithFaults` 活動使用 <xref:System.Activities.Statements.FlowSwitch%601> 活動，在 `promoCode` 引數上切換，並透過下列公式計算折扣。</span><span class="sxs-lookup"><span data-stu-id="211d4-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="211d4-120">`promoCode` 的值</span><span class="sxs-lookup"><span data-stu-id="211d4-120">Value of `promoCode`</span></span>|<span data-ttu-id="211d4-121">折扣 (%)</span><span class="sxs-lookup"><span data-stu-id="211d4-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="211d4-122">Single</span><span class="sxs-lookup"><span data-stu-id="211d4-122">Single</span></span>|<span data-ttu-id="211d4-123">10</span><span class="sxs-lookup"><span data-stu-id="211d4-123">10</span></span>|
|<span data-ttu-id="211d4-124">MNK</span><span class="sxs-lookup"><span data-stu-id="211d4-124">MNK</span></span>|<span data-ttu-id="211d4-125">15</span><span class="sxs-lookup"><span data-stu-id="211d4-125">15</span></span>|
|<span data-ttu-id="211d4-126">MWK</span><span class="sxs-lookup"><span data-stu-id="211d4-126">MWK</span></span>|<span data-ttu-id="211d4-127">15 + (1 – 1 /`numberOfKids`)\*10**注意：** 甚至是此計算可能會擲回<xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="211d4-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="211d4-128">因此，折扣計算是包裝在 <xref:System.Activities.Statements.TryCatch> 活動中，以攔截 <xref:System.DivideByZeroException> 例外狀況並將折扣設為零。</span><span class="sxs-lookup"><span data-stu-id="211d4-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="211d4-129">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="211d4-129">To use this sample</span></span>

1.  <span data-ttu-id="211d4-130">使用 Visual Studio 2010 開啟 FlowchartWithFaultHandling.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="211d4-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2.  <span data-ttu-id="211d4-131">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="211d4-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="211d4-132">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="211d4-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="211d4-133">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="211d4-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="211d4-134">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="211d4-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="211d4-135">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="211d4-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="211d4-136">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="211d4-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="211d4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="211d4-137">See Also</span></span>  
 [<span data-ttu-id="211d4-138">流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="211d4-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="211d4-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="211d4-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
