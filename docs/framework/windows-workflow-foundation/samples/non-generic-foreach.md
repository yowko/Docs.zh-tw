---
title: 非泛型 ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 0274cd5b87e6039ff40afa3108986ffd113fc4fb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089617"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="b57e6-102">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="b57e6-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="b57e6-103"> 的工具箱中隨附一組控制流程活動，包括允許逐一查看 <xref:System.Activities.Statements.ForEach%601> 集合的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="b57e6-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="b57e6-104"><xref:System.Activities.Statements.ForEach%601> 的 <xref:System.Activities.Statements.ForEach%601.Values%2A> 屬性必須是 <xref:System.Collections.Generic.IEnumerable%601> 型別。</span><span class="sxs-lookup"><span data-stu-id="b57e6-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b57e6-105">這會防止使用者逐一查看實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的資料結構 (例如 <xref:System.Collections.ArrayList>)。</span><span class="sxs-lookup"><span data-stu-id="b57e6-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="b57e6-106">非泛型 <xref:System.Activities.Statements.ForEach%601> 版本沒有這項需求，但在執行階段更複雜，以確保集合中數值型別的相容性。</span><span class="sxs-lookup"><span data-stu-id="b57e6-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="b57e6-107">這個範例示範如何實作非泛型 <xref:System.Activities.Statements.ForEach%601> 活動及其設計工具。</span><span class="sxs-lookup"><span data-stu-id="b57e6-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="b57e6-108">這個活動可用來逐一查看 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="b57e6-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="b57e6-109">ForEach 活動</span><span class="sxs-lookup"><span data-stu-id="b57e6-109">ForEach Activity</span></span>  
 <span data-ttu-id="b57e6-110">C#/VB `foreach` 陳述式會列舉集合項目，並針對集合的每個項目執行內嵌陳述式。</span><span class="sxs-lookup"><span data-stu-id="b57e6-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="b57e6-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 的 `foreach` 對應活動為 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="b57e6-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="b57e6-112"><xref:System.Activities.Statements.ForEach%601> 活動包含值清單和主體。</span><span class="sxs-lookup"><span data-stu-id="b57e6-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="b57e6-113">在執行階段，會列舉此清單，並針對清單中的每個值執行主體。</span><span class="sxs-lookup"><span data-stu-id="b57e6-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="b57e6-114">在大部分情況下，泛型活動版本應該是慣用方案，因為它涵蓋大部分使用狀況，也提供編譯階段的類型檢查。</span><span class="sxs-lookup"><span data-stu-id="b57e6-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="b57e6-115">非泛型版本可用來逐一查看實作非泛型 <xref:System.Collections.IEnumerable> 介面的型別。</span><span class="sxs-lookup"><span data-stu-id="b57e6-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="b57e6-116">類別定義</span><span class="sxs-lookup"><span data-stu-id="b57e6-116">Class Definition</span></span>  
 <span data-ttu-id="b57e6-117">下列程式碼範例示範非泛型 `ForEach` 活動的定義。</span><span class="sxs-lookup"><span data-stu-id="b57e6-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 <span data-ttu-id="b57e6-118">Body (選擇性)</span><span class="sxs-lookup"><span data-stu-id="b57e6-118">Body (optional)</span></span>  
 <span data-ttu-id="b57e6-119"><xref:System.Activities.ActivityAction> 型別的 <xref:System.Object>，針對集合中的每個項目來執行。</span><span class="sxs-lookup"><span data-stu-id="b57e6-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="b57e6-120">每個個別項目透過 `Argument` 屬性傳遞至 Body。</span><span class="sxs-lookup"><span data-stu-id="b57e6-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="b57e6-121">Values (選擇性)</span><span class="sxs-lookup"><span data-stu-id="b57e6-121">Values (optional)</span></span>  
 <span data-ttu-id="b57e6-122">逐一查看的項目集合。</span><span class="sxs-lookup"><span data-stu-id="b57e6-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="b57e6-123">確認所有集合項目具有相容型別的作業是在執行階段進行。</span><span class="sxs-lookup"><span data-stu-id="b57e6-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="b57e6-124">使用 ForEach 的範例</span><span class="sxs-lookup"><span data-stu-id="b57e6-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="b57e6-125">下列程式碼示範如何在應用程式中使用 ForEach 活動。</span><span class="sxs-lookup"><span data-stu-id="b57e6-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|<span data-ttu-id="b57e6-126">條件</span><span class="sxs-lookup"><span data-stu-id="b57e6-126">Condition</span></span>|<span data-ttu-id="b57e6-127">訊息</span><span class="sxs-lookup"><span data-stu-id="b57e6-127">Message</span></span>|<span data-ttu-id="b57e6-128">嚴重性</span><span class="sxs-lookup"><span data-stu-id="b57e6-128">Severity</span></span>|<span data-ttu-id="b57e6-129">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="b57e6-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="b57e6-130">Values 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="b57e6-130">Values is `null`</span></span>|<span data-ttu-id="b57e6-131">未提供必要活動引數 'Values' 的值。</span><span class="sxs-lookup"><span data-stu-id="b57e6-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="b57e6-132">錯誤</span><span class="sxs-lookup"><span data-stu-id="b57e6-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="b57e6-133">ForEach 設計工具</span><span class="sxs-lookup"><span data-stu-id="b57e6-133">ForEach Designer</span></span>  
 <span data-ttu-id="b57e6-134">此範例的活動設計工具在外觀上與針對內建 <xref:System.Activities.Statements.ForEach%601> 活動所提供的設計工具類似。</span><span class="sxs-lookup"><span data-stu-id="b57e6-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="b57e6-135">在工具箱 中的設計工具隨即出現**範例**，**非泛型活動**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b57e6-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="b57e6-136">名為設計工具**ForEachWithBodyFactory**在工具箱中，因為活動會公開<xref:System.Activities.Presentation.IActivityTemplateFactory>在工具箱中，這會建立活動有適當設定<xref:System.Activities.ActivityAction>。</span><span class="sxs-lookup"><span data-stu-id="b57e6-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="b57e6-137">若要執行這個範例</span><span class="sxs-lookup"><span data-stu-id="b57e6-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="b57e6-138">將您選擇的專案設定為方案的啟始專案：</span><span class="sxs-lookup"><span data-stu-id="b57e6-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="b57e6-139">**CodeTestClient**示範如何使用使用程式碼的活動。</span><span class="sxs-lookup"><span data-stu-id="b57e6-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="b57e6-140">**DesignerTestClient**示範如何使用設計工具內的活動。</span><span class="sxs-lookup"><span data-stu-id="b57e6-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="b57e6-141">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="b57e6-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b57e6-142">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b57e6-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b57e6-143">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b57e6-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b57e6-144">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="b57e6-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b57e6-145">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b57e6-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
