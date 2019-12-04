---
title: 非泛型 ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715636"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="45e92-102">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="45e92-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="45e92-103">的工具箱中隨附一組控制流程活動，包括允許逐一查看 <xref:System.Activities.Statements.ParallelForEach%601> 集合的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="45e92-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="45e92-104"><xref:System.Activities.Statements.ParallelForEach%601> 需要其 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> 屬性屬於類型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="45e92-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="45e92-105">這會防止使用者逐一查看實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的資料結構 (例如 <xref:System.Collections.ArrayList>)。</span><span class="sxs-lookup"><span data-stu-id="45e92-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="45e92-106">非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 版本沒有這項需求，但在執行階段更複雜，以確保集合中數值型別的相容性。</span><span class="sxs-lookup"><span data-stu-id="45e92-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="45e92-107">這個範例示範如何實作非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動及其設計工具。</span><span class="sxs-lookup"><span data-stu-id="45e92-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="45e92-108">這個活動可用來逐一查看 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="45e92-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="45e92-109">ParallelForEach 活動</span><span class="sxs-lookup"><span data-stu-id="45e92-109">ParallelForEach activity</span></span>

<span data-ttu-id="45e92-110">C#/VB `foreach` 陳述式會列舉集合項目，並針對集合的每個項目執行內嵌陳述式。</span><span class="sxs-lookup"><span data-stu-id="45e92-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="45e92-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 對應活動為 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="45e92-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="45e92-112"><xref:System.Activities.Statements.ForEach%601> 活動包含值清單和主體。</span><span class="sxs-lookup"><span data-stu-id="45e92-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="45e92-113">在執行階段，會列舉此清單，並針對清單中的每個值執行主體。</span><span class="sxs-lookup"><span data-stu-id="45e92-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="45e92-114"><xref:System.Activities.Statements.ParallelForEach%601> 具有 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，所以如果 <xref:System.Activities.Statements.ParallelForEach%601> 的評估傳回 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，`true` 活動就可以早一點完成。</span><span class="sxs-lookup"><span data-stu-id="45e92-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="45e92-115">在每次反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>。</span><span class="sxs-lookup"><span data-stu-id="45e92-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="45e92-116">在大部分情況下，泛型版本的活動應該是慣用方案，因為它涵蓋大部分使用狀況，也提供編譯階段的型別檢查。</span><span class="sxs-lookup"><span data-stu-id="45e92-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="45e92-117">非泛型版本可用來逐一查看實作非泛型 <xref:System.Collections.IEnumerable> 介面的型別。</span><span class="sxs-lookup"><span data-stu-id="45e92-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="45e92-118">類別定義</span><span class="sxs-lookup"><span data-stu-id="45e92-118">Class definition</span></span>

<span data-ttu-id="45e92-119">下列程式碼範例示範非泛型 `ParallelForEach` 活動的定義。</span><span class="sxs-lookup"><span data-stu-id="45e92-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="45e92-120">Body （選擇性） </span><span class="sxs-lookup"><span data-stu-id="45e92-120">Body (optional)</span></span>\
<span data-ttu-id="45e92-121"><xref:System.Activities.ActivityAction> 型別的 <xref:System.Object>，針對集合中的每個項目來執行。</span><span class="sxs-lookup"><span data-stu-id="45e92-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="45e92-122">每個個別項目都會透過 Argument 屬性傳遞至 Body。</span><span class="sxs-lookup"><span data-stu-id="45e92-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="45e92-123">值（選擇性） </span><span class="sxs-lookup"><span data-stu-id="45e92-123">Values (optional)</span></span>\
<span data-ttu-id="45e92-124">逐一查看的項目集合。</span><span class="sxs-lookup"><span data-stu-id="45e92-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="45e92-125">確認所有集合項目具有相容型別的作業是在執行階段進行。</span><span class="sxs-lookup"><span data-stu-id="45e92-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="45e92-126">CompletionCondition （選擇性） </span><span class="sxs-lookup"><span data-stu-id="45e92-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="45e92-127">在任何反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="45e92-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="45e92-128">如果評估為 `true`，則會取消已排程的擱置中反覆運算。</span><span class="sxs-lookup"><span data-stu-id="45e92-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="45e92-129">如果並未設定此屬性，則分支集合中的所有活動會執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="45e92-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="45e92-130">使用 ParallelForEach 的範例</span><span class="sxs-lookup"><span data-stu-id="45e92-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="45e92-131">下列程式碼示範如何在應用程式中使用 ParallelForEach 活動。</span><span class="sxs-lookup"><span data-stu-id="45e92-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="45e92-132">ParallelForEach 設計工具</span><span class="sxs-lookup"><span data-stu-id="45e92-132">ParallelForEach designer</span></span>

<span data-ttu-id="45e92-133">此範例的活動設計工具在外觀上與針對內建 <xref:System.Activities.Statements.ParallelForEach%601> 活動所提供的設計工具類似。</span><span class="sxs-lookup"><span data-stu-id="45e92-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="45e92-134">設計工具會出現在 [**範例**]、[**非泛型活動**] 分類的 [工具箱] 中。</span><span class="sxs-lookup"><span data-stu-id="45e92-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="45e92-135">設計工具會在 [工具箱] 中命名為**ParallelForEachWithBodyFactory** ，因為活動會在 [工具箱] 中公開 <xref:System.Activities.Presentation.IActivityTemplateFactory>，以使用正確設定的 <xref:System.Activities.ActivityAction>來建立活動。</span><span class="sxs-lookup"><span data-stu-id="45e92-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="45e92-136">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="45e92-136">To run the sample</span></span>

1. <span data-ttu-id="45e92-137">將您選擇的專案設定為方案的啟始專案。</span><span class="sxs-lookup"><span data-stu-id="45e92-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="45e92-138">**CodeTestClient**顯示如何使用程式碼來使用活動。</span><span class="sxs-lookup"><span data-stu-id="45e92-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="45e92-139">**DesignerTestClient**顯示如何在設計工具中使用活動。</span><span class="sxs-lookup"><span data-stu-id="45e92-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="45e92-140">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="45e92-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45e92-141">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="45e92-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45e92-142">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="45e92-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="45e92-143">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="45e92-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45e92-144">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="45e92-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
