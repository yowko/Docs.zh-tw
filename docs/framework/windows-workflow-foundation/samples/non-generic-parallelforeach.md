---
title: 非泛型 ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 0bdaaac04162cf065d847f5071ba21953f042223
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519385"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="2b5fb-102">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="2b5fb-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="2b5fb-103"> 工具箱中隨附一組控制流程活動，包括<xref:System.Activities.Statements.ParallelForEach%601>，允許逐一<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`集合。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="2b5fb-104"><xref:System.Activities.Statements.ParallelForEach%601> 需要其<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>屬性型別<!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="2b5fb-105">這會防止使用者逐一查看實作資料結構<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`介面 (例如， <xref:System.Collections.ArrayList>)。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="2b5fb-106">非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 版本沒有這項需求，但在執行階段更複雜，以確保集合中數值型別的相容性。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="2b5fb-107">這個範例示範如何實作非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動及其設計工具。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="2b5fb-108">這個活動可用來逐一查看 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="2b5fb-109">ParallelForEach 活動</span><span class="sxs-lookup"><span data-stu-id="2b5fb-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="2b5fb-110">C#/VB `foreach` 陳述式會列舉集合項目，並針對集合的每個項目執行內嵌陳述式。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="2b5fb-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 對應活動為 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="2b5fb-112"><xref:System.Activities.Statements.ForEach%601> 活動包含值清單和主體。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="2b5fb-113">在執行階段，會列舉此清單，並針對清單中的每個值執行主體。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="2b5fb-114"><xref:System.Activities.Statements.ParallelForEach%601> 具有 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，所以如果 <xref:System.Activities.Statements.ParallelForEach%601> 的評估傳回 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，`true` 活動就可以早一點完成。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="2b5fb-115">在每次反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="2b5fb-116">在大部分情況下，泛型版本的活動應該是慣用方案，因為它涵蓋大部分使用狀況，也提供編譯階段的型別檢查。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="2b5fb-117">非泛型版本可用來逐一查看實作非泛型 <xref:System.Collections.IEnumerable> 介面的型別。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="2b5fb-118">類別定義</span><span class="sxs-lookup"><span data-stu-id="2b5fb-118">Class Definition</span></span>  
 <span data-ttu-id="2b5fb-119">下列程式碼範例示範非泛型 `ParallelForEach` 活動的定義。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
```  
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
  
 <span data-ttu-id="2b5fb-120">Body (選擇性)</span><span class="sxs-lookup"><span data-stu-id="2b5fb-120">Body (optional)</span></span>  
 <span data-ttu-id="2b5fb-121"><xref:System.Activities.ActivityAction> 型別的 <xref:System.Object>，針對集合中的每個項目來執行。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="2b5fb-122">每個個別項目都會透過 Argument 屬性傳遞至 Body。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="2b5fb-123">Values (選擇性)</span><span class="sxs-lookup"><span data-stu-id="2b5fb-123">Values (optional)</span></span>  
 <span data-ttu-id="2b5fb-124">逐一查看的項目集合。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="2b5fb-125">確認所有集合項目具有相容型別的作業是在執行階段進行。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="2b5fb-126">CompletionCondition (選擇性)</span><span class="sxs-lookup"><span data-stu-id="2b5fb-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="2b5fb-127">在任何反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="2b5fb-128">如果評估為 `true`，則會取消已排程的擱置中反覆運算。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="2b5fb-129">如果並未設定此屬性，則分支集合中的所有活動會執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="2b5fb-130">使用 ParallelForEach 的範例</span><span class="sxs-lookup"><span data-stu-id="2b5fb-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="2b5fb-131">下列程式碼示範如何在應用程式中使用 ParallelForEach 活動。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
```  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="2b5fb-132">ParallelForEach 設計工具</span><span class="sxs-lookup"><span data-stu-id="2b5fb-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="2b5fb-133">此範例的活動設計工具在外觀上與針對內建 <xref:System.Activities.Statements.ParallelForEach%601> 活動所提供的設計工具類似。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="2b5fb-134">設計工具隨即出現在工具箱的**範例**，**非泛型活動**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="2b5fb-135">在設計工具名為**ParallelForEachWithBodyFactory**在工具箱中，因為活動會公開<xref:System.Activities.Presentation.IActivityTemplateFactory>建立有適當設定活動工具箱 中<xref:System.Activities.ActivityAction>。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="2b5fb-136">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="2b5fb-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="2b5fb-137">將您選擇的專案設定為方案的啟始專案。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="2b5fb-138">**CodeTestClient**示範如何透過程式碼使用活動。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="2b5fb-139">**DesignerTestClient**示範如何使用設計工具內的活動。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="2b5fb-140">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b5fb-141">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2b5fb-142">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2b5fb-143">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b5fb-144">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2b5fb-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
