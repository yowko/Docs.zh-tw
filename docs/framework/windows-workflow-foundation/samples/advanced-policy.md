---
title: "進階原則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c83f4167ce1947b10f97e0cab5b5ddd2f8e00c76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-policy"></a><span data-ttu-id="74c98-102">進階原則</span><span class="sxs-lookup"><span data-stu-id="74c98-102">Advanced Policy</span></span>
<span data-ttu-id="74c98-103">這個範例會延續簡單原則範例。</span><span class="sxs-lookup"><span data-stu-id="74c98-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="74c98-104">除了簡單原則範例的住家折扣和商務折扣規則外，還新增數個規則。</span><span class="sxs-lookup"><span data-stu-id="74c98-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="74c98-105">新增了高額規則，為高額訂單提供更大的折扣。</span><span class="sxs-lookup"><span data-stu-id="74c98-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="74c98-106">此規則的優先順序值小於前兩個規則，因此它會覆寫折扣欄位，並且優先順序高於住家及商務折扣規則。</span><span class="sxs-lookup"><span data-stu-id="74c98-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="74c98-107">此外，還新增了計算總額規則，此規則會根據折扣等級計算總額，</span><span class="sxs-lookup"><span data-stu-id="74c98-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="74c98-108">並說明如何參考工作流程活動定義的方法，以及如何使用其他動作。</span><span class="sxs-lookup"><span data-stu-id="74c98-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="74c98-109">這個規則還會示範鏈結行為，因為每當折扣欄位變更時，就會評估一次。</span><span class="sxs-lookup"><span data-stu-id="74c98-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="74c98-110">此外，CalculateTotal 方法的方法屬性設定顯示為 RuleWriteAttribute。</span><span class="sxs-lookup"><span data-stu-id="74c98-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="74c98-111">這使得每次執行方法時，都會重新評估受影響的規則 (ErrorTotalRule)。</span><span class="sxs-lookup"><span data-stu-id="74c98-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="74c98-112">最後新增的規則是偵測錯誤的規則 (在此例中，Total 小於 0)。</span><span class="sxs-lookup"><span data-stu-id="74c98-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="74c98-113">如果偵測到錯誤，就會暫止執行原則。</span><span class="sxs-lookup"><span data-stu-id="74c98-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="74c98-114">最後，將 `Console.Writeline` 呼叫當做動作新增至每個規則，以提高規則執行的可視性，而且這也表示可以存取參照類型上的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="74c98-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="74c98-115">您也可以使用追蹤來取得所執行規則的可視性。</span><span class="sxs-lookup"><span data-stu-id="74c98-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="74c98-116">這個範例使用的規則包括：</span><span class="sxs-lookup"><span data-stu-id="74c98-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="74c98-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="74c98-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="74c98-118">IF OrderValue > 500 AND CustomerType = Residential</span><span class="sxs-lookup"><span data-stu-id="74c98-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="74c98-119">THEN Discount = 5%</span><span class="sxs-lookup"><span data-stu-id="74c98-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="74c98-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="74c98-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="74c98-121">IF OrderValue > 10000 AND CustomerType = Business</span><span class="sxs-lookup"><span data-stu-id="74c98-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="74c98-122">THEN Discount = 10%</span><span class="sxs-lookup"><span data-stu-id="74c98-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="74c98-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="74c98-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="74c98-124">IF OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="74c98-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="74c98-125">THEN Discount = 15%</span><span class="sxs-lookup"><span data-stu-id="74c98-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="74c98-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="74c98-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="74c98-127">IF Discount > 0</span><span class="sxs-lookup"><span data-stu-id="74c98-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="74c98-128">THEN CalculateTotal(OrderValue, Discount)</span><span class="sxs-lookup"><span data-stu-id="74c98-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="74c98-129">ELSE Total = OrderValue</span><span class="sxs-lookup"><span data-stu-id="74c98-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="74c98-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="74c98-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="74c98-131">如果總\<0</span><span class="sxs-lookup"><span data-stu-id="74c98-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="74c98-132">THEN Error = "Fired ErrorTotalRule"; Halt</span><span class="sxs-lookup"><span data-stu-id="74c98-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="74c98-133">透過追蹤，您還可以觀察到規則的評估和執行。</span><span class="sxs-lookup"><span data-stu-id="74c98-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="74c98-134">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="74c98-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="74c98-135">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="74c98-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="74c98-136">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="74c98-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="74c98-137">按 CTRL+F5 執行方案，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="74c98-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="74c98-138">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="74c98-138">To run the sample</span></span>  
  
-   <span data-ttu-id="74c98-139">在 [SDK 命令提示字元] 視窗中，執行 AdvancedPolicy\bin\debug 資料夾 (若是範例的 Visual Basic 版本，則是 AdvancedPolicy \bin 資料夾) 中的 .exe 檔案，該資料夾位於此範例的主要資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="74c98-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74c98-140">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="74c98-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="74c98-141">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="74c98-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74c98-142">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="74c98-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74c98-143">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="74c98-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="74c98-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="74c98-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="74c98-145">簡單原則</span><span class="sxs-lookup"><span data-stu-id="74c98-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
