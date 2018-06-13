---
title: 進階原則
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: 81cf2fb428833d4ca8cccf197011b69f2ccf3108
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515551"
---
# <a name="advanced-policy"></a><span data-ttu-id="3f0a5-102">進階原則</span><span class="sxs-lookup"><span data-stu-id="3f0a5-102">Advanced Policy</span></span>
<span data-ttu-id="3f0a5-103">這個範例會延續簡單原則範例。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="3f0a5-104">除了簡單原則範例的住家折扣和商務折扣規則外，還新增數個規則。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="3f0a5-105">新增了高額規則，為高額訂單提供更大的折扣。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="3f0a5-106">此規則的優先順序值小於前兩個規則，因此它會覆寫折扣欄位，並且優先順序高於住家及商務折扣規則。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="3f0a5-107">此外，還新增了計算總額規則，此規則會根據折扣等級計算總額，</span><span class="sxs-lookup"><span data-stu-id="3f0a5-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="3f0a5-108">並說明如何參考工作流程活動定義的方法，以及如何使用其他動作。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="3f0a5-109">這個規則還會示範鏈結行為，因為每當折扣欄位變更時，就會評估一次。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="3f0a5-110">此外，CalculateTotal 方法的方法屬性設定顯示為 RuleWriteAttribute。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="3f0a5-111">這使得每次執行方法時，都會重新評估受影響的規則 (ErrorTotalRule)。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="3f0a5-112">最後新增的規則是偵測錯誤的規則 (在此例中，Total 小於 0)。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="3f0a5-113">如果偵測到錯誤，就會暫止執行原則。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="3f0a5-114">最後，將 `Console.Writeline` 呼叫當做動作新增至每個規則，以提高規則執行的可視性，而且這也表示可以存取參照類型上的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="3f0a5-115">您也可以使用追蹤來取得所執行規則的可視性。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="3f0a5-116">這個範例使用的規則包括：</span><span class="sxs-lookup"><span data-stu-id="3f0a5-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="3f0a5-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="3f0a5-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="3f0a5-118">IF OrderValue > 500 AND CustomerType = Residential</span><span class="sxs-lookup"><span data-stu-id="3f0a5-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="3f0a5-119">THEN Discount = 5%</span><span class="sxs-lookup"><span data-stu-id="3f0a5-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="3f0a5-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="3f0a5-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="3f0a5-121">IF OrderValue > 10000 AND CustomerType = Business</span><span class="sxs-lookup"><span data-stu-id="3f0a5-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="3f0a5-122">THEN Discount = 10%</span><span class="sxs-lookup"><span data-stu-id="3f0a5-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="3f0a5-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="3f0a5-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="3f0a5-124">IF OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="3f0a5-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="3f0a5-125">THEN Discount = 15%</span><span class="sxs-lookup"><span data-stu-id="3f0a5-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="3f0a5-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="3f0a5-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="3f0a5-127">IF Discount > 0</span><span class="sxs-lookup"><span data-stu-id="3f0a5-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="3f0a5-128">THEN CalculateTotal(OrderValue, Discount)</span><span class="sxs-lookup"><span data-stu-id="3f0a5-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="3f0a5-129">ELSE Total = OrderValue</span><span class="sxs-lookup"><span data-stu-id="3f0a5-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="3f0a5-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="3f0a5-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="3f0a5-131">如果總\<0</span><span class="sxs-lookup"><span data-stu-id="3f0a5-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="3f0a5-132">THEN Error = "Fired ErrorTotalRule"; Halt</span><span class="sxs-lookup"><span data-stu-id="3f0a5-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="3f0a5-133">透過追蹤，您還可以觀察到規則的評估和執行。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="3f0a5-134">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="3f0a5-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="3f0a5-135">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3f0a5-136">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3f0a5-137">按 CTRL+F5 執行方案，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3f0a5-138">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="3f0a5-138">To run the sample</span></span>  
  
-   <span data-ttu-id="3f0a5-139">在 [SDK 命令提示字元] 視窗中，執行 AdvancedPolicy\bin\debug 資料夾 (若是範例的 Visual Basic 版本，則是 AdvancedPolicy \bin 資料夾) 中的 .exe 檔案，該資料夾位於此範例的主要資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f0a5-140">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3f0a5-141">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="3f0a5-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3f0a5-142">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="3f0a5-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f0a5-143">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="3f0a5-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="3f0a5-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f0a5-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="3f0a5-145">簡單原則</span><span class="sxs-lookup"><span data-stu-id="3f0a5-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
