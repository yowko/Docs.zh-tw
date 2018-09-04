---
title: 自訂活動以切換到值的範圍
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563396"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="6e31f-102">自訂活動以切換到值的範圍</span><span class="sxs-lookup"><span data-stu-id="6e31f-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="6e31f-103">這個範例示範如何建立可擴充 <xref:System.Activities.Statements.Switch%601> 用法的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="6e31f-104">傳統 <xref:System.Activities.Statements.Switch%601> 陳述式允許根據單一值的切換。</span><span class="sxs-lookup"><span data-stu-id="6e31f-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="6e31f-105">但有些商務狀況中活動必須根據值範圍來切換。</span><span class="sxs-lookup"><span data-stu-id="6e31f-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="6e31f-106">例如，當切換依據的值介於 1 和 5 之間時，活動可能會執行某個動作，當值介於 6 和 10 之間時執行另一個動作，並針對所有其他值執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="6e31f-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="6e31f-107">這個自訂活動正是實現該狀況。</span><span class="sxs-lookup"><span data-stu-id="6e31f-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="6e31f-108">SwitchRange 活動</span><span class="sxs-lookup"><span data-stu-id="6e31f-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="6e31f-109">`SwitchRange` 活動會在其運算式的結果值是包含在其中一個 `Cases` 的範圍時排定子活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="6e31f-110">下列程式碼範例為根據值範圍來切換的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="6e31f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6e31f-111">Property</span></span>|<span data-ttu-id="6e31f-112">描述</span><span class="sxs-lookup"><span data-stu-id="6e31f-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="6e31f-113">運算式</span><span class="sxs-lookup"><span data-stu-id="6e31f-113">Expression</span></span>|<span data-ttu-id="6e31f-114">這是要進行評估並與 Cases 清單中的範圍進行比較的運算式。</span><span class="sxs-lookup"><span data-stu-id="6e31f-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="6e31f-115">運算式的結果為 T 類型。</span><span class="sxs-lookup"><span data-stu-id="6e31f-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="6e31f-116">Cases</span><span class="sxs-lookup"><span data-stu-id="6e31f-116">Cases</span></span>|<span data-ttu-id="6e31f-117">每個案例包含範圍 (From 和 To) 以及活動 (Body)。</span><span class="sxs-lookup"><span data-stu-id="6e31f-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="6e31f-118">運算式會進行評估並與範圍進行比較。</span><span class="sxs-lookup"><span data-stu-id="6e31f-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="6e31f-119">如果運算式結果是在其中一個案例的範圍中，則會執行對應活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="6e31f-120">預設</span><span class="sxs-lookup"><span data-stu-id="6e31f-120">Default</span></span>|<span data-ttu-id="6e31f-121">當沒有相符案例時執行的活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="6e31f-122">設為 `null` 時，不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="6e31f-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="6e31f-123">CaseRange 類別</span><span class="sxs-lookup"><span data-stu-id="6e31f-123">CaseRange Class</span></span>  
 <span data-ttu-id="6e31f-124">`CaseRange` 類別代表 `SwitchRange` 活動中的範圍。</span><span class="sxs-lookup"><span data-stu-id="6e31f-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="6e31f-125">每個 `CaseRange` 執行個體都包含範圍 (由 `From` 和 `To` 組成) 以及 `Body` 活動 (當 `SwitchRange` 中的運算式評估結果是在範圍中時排程的活動)。</span><span class="sxs-lookup"><span data-stu-id="6e31f-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="6e31f-126">下列程式碼範例是 `CaseRange` 類別的定義。</span><span class="sxs-lookup"><span data-stu-id="6e31f-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="6e31f-127">此範例中定義的 `SwitchRange` 和 `CaseRange` 類別都是可與實作 `IComparable` 的任何類型 (如 <xref:System.Activities.Statements.Switch%601> 類別) 搭配使用的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="6e31f-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="6e31f-128">範例用法</span><span class="sxs-lookup"><span data-stu-id="6e31f-128">Sample Usage</span></span>  
 <span data-ttu-id="6e31f-129">下列程式碼範例會示範如何使用 `SwitchRange` 活動。</span><span class="sxs-lookup"><span data-stu-id="6e31f-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6e31f-130">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6e31f-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="6e31f-131">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 SwitchRange.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6e31f-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6e31f-132">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="6e31f-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6e31f-133">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="6e31f-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e31f-134">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6e31f-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6e31f-135">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6e31f-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6e31f-136">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6e31f-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e31f-137">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6e31f-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`