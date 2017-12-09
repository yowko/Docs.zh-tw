---
title: "C# 運算式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f220ffdf04102a110124e7331a53ae5ee70316a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="c-expressions"></a><span data-ttu-id="0f865-102">C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-102">C# Expressions</span></span>
<span data-ttu-id="0f865-103">從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，[!INCLUDE[wf](../../../includes/wf-md.md)] 支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="0f865-104">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中所建立之新 C# 工作流程專案，以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標，使用 C# 運算式，而 Visual Basic 工作流程專案則使用 Visual Basic 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="0f865-105">不論是否支援專案語言，使用 Visual Basic 運算式的現有 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 工作流程專案均可移轉至 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0f865-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="0f865-106">本主題提供 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的 C# 運算式概觀。</span><span class="sxs-lookup"><span data-stu-id="0f865-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="0f865-107">在工作流程中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="0f865-108">在工作流程設計工具中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="0f865-109">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="0f865-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="0f865-110">在程式碼工作流程中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="0f865-111">在 XAML 工作流程中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="0f865-112">編譯的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="0f865-113">鬆散的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="0f865-114">在 XAMLX 工作流程服務中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a><span data-ttu-id="0f865-115">在工作流程設計工具中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-115">Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="0f865-116">從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，[!INCLUDE[wf](../../../includes/wf-md.md)] 支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="0f865-117">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中所建立之新 C# 工作流程專案，以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的，使用 C# 運算式，而 Visual Basic 工作流程專案則使用 Visual Basic 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="0f865-118">若要指定所需的 C# 運算式，方塊中輸入標記為**輸入 C# 運算式**。</span><span class="sxs-lookup"><span data-stu-id="0f865-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="0f865-119">在設計工具中選取活動時，會在屬性視窗中顯示此標籤，而此標籤也會顯示在工作流程設計工具中的活動之上。</span><span class="sxs-lookup"><span data-stu-id="0f865-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="0f865-120">在下列範例中，`WriteLine` 內的 `Sequence` 包含兩個 `NoPersistScope` 活動。</span><span class="sxs-lookup"><span data-stu-id="0f865-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="0f865-121">![自動建立序列活動](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="0f865-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f865-122">只有在 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 中才支援 C# 運算式，重新裝載的工作流程設計工具不支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-122">C# expressions are supported only in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0f865-123">新的重新裝載設計工具中，支援的 WF45 功能，請參閱[新 Workflow Foundation 4.5 功能，在重新裝載工作流程設計工具中支援](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="0f865-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <a name="BackwardCompat"></a><span data-ttu-id="0f865-124">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="0f865-124">Backwards compatibility</span></span>  
 <span data-ttu-id="0f865-125">支援已移轉至 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 之現有 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# 工作流程專案中的 Visual Basic 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="0f865-126">當工作流程設計工具中檢視 Visual Basic 運算式時，取代現有的 Visual Basic 運算式的文字**XAML 中的值已設定**，除非您的 Visual Basic 運算式是有效的 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="0f865-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="0f865-127">如果 Visual Basic 運算式為有效的 C# 語法，則會顯示該運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="0f865-128">若要將 Visual Basic 運算式更新為 C#，您可以在工作流程設計工具中編輯這些運算式，並指定相等的 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="0f865-129">您不需要將 Visual Basic 運算式更新為 C#，不過一旦這些運算式在工作流程設計工具中更新，將會轉換為 C#，且可能無法還原為 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="0f865-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <a name="CodeWorkflows"></a><span data-ttu-id="0f865-130">在程式碼工作流程中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-130">Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="0f865-131">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 程式碼為主的工作流程支援 C# 運算式，但是您必須使用 <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> 編譯 C# 運算式，工作流程才能叫用運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f865-132">工作流程作者可以使用 `CSharpValue` 來表示運算式的右值 (r-value)，並使用 `CSharpReference` 來表示運算式的左值 (l-value)。</span><span class="sxs-lookup"><span data-stu-id="0f865-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="0f865-133">下列範例使用 `Assign` 活動內含的 `WriteLine` 活動和 `Sequence` 活動，來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="0f865-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="0f865-134">該範例為 `CSharpReference` 的 `To` 引數，指定一個 `Assign`，表示運算式的左值。</span><span class="sxs-lookup"><span data-stu-id="0f865-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="0f865-135">`CSharpValue` 的 `Value` 引數和 `Assign` 的 `Text` 引數指定一個 `WriteLine`，表示這兩個運算式的右值。</span><span class="sxs-lookup"><span data-stu-id="0f865-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
```csharp  
Variable<int> n = new Variable<int>  
{  
    Name = "n"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { n },  
    Activities =  
    {  
        new Assign<int>  
        {  
            To = new CSharpReference<int>("n"),  
            Value = new CSharpValue<int>("new Random().Next(1, 101)")  
        },  
        new WriteLine  
        {  
            Text = new CSharpValue<string>("\"The number is \" + n")  
        }  
    }  
};  
  
CompileExpressions(wf);  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="0f865-136">建構工作流程之後，會呼叫 `CompileExpressions` Helper 方法來編譯 C# 運算式，然後叫用工作流程。</span><span class="sxs-lookup"><span data-stu-id="0f865-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="0f865-137">以下範例是 `CompileExpressions` 方法。</span><span class="sxs-lookup"><span data-stu-id="0f865-137">The following example is the `CompileExpressions` method.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="0f865-138">如果未編譯 C# 運算式，<xref:System.NotSupportedException>叫用工作流程與下列類似的訊息時，會擲回： `Expression Activity type 'CSharpValue`1' 需要編譯才能執行。</span><span class="sxs-lookup"><span data-stu-id="0f865-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="0f865-139">請確定已編譯工作流程。 '</span><span class="sxs-lookup"><span data-stu-id="0f865-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="0f865-140">如果您的自訂程式碼為主之工作流程使用 `DynamicActivity`，則需要對 `CompileExpressions` 方法進行一些變更，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f865-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
```csharp  
static void CompileExpressions(DynamicActivity dynamicActivity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions. For Dynamic Activities this can be retrieved using the  
    // name property , which must be in the form Namespace.Type.  
    string activityName = dynamicActivity.Name;  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = dynamicActivity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = true  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(  
        dynamicActivity, compiledExpressionRoot);  
}  
```  
  
 <span data-ttu-id="0f865-141">在動態活動中編譯 C# 運算式的 `CompileExpressions` 多載有一些差異。</span><span class="sxs-lookup"><span data-stu-id="0f865-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="0f865-142">傳給 `CompileExpressions` 的參數為 `DynamicActivity`。</span><span class="sxs-lookup"><span data-stu-id="0f865-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="0f865-143">擷取型別名稱和命名空間需使用 `DynamicActivity.Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f865-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="0f865-144">`TextExpressionCompilerSettings.ForImplementation` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="0f865-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="0f865-145">呼叫 `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`，而不是 `CompiledExpressionInvoker.SetCompiledExpressionRoot`。</span><span class="sxs-lookup"><span data-stu-id="0f865-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0f865-146">使用程式碼中的運算式，請參閱 <<c2> [ 撰寫工作流程、 活動和運算式使用命令式程式碼](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="0f865-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <a name="XamlWorkflows"></a><span data-ttu-id="0f865-147">在 XAML 工作流程中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-147">Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="0f865-148">XAML 工作流程支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="0f865-149">編譯的 XAML 工作流程會編譯為型別，而鬆散的 XAML 工作流程會在工作流程執行時，由執行階段載入並編譯為活動樹狀。</span><span class="sxs-lookup"><span data-stu-id="0f865-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="0f865-150">編譯的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="0f865-151">鬆散的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a><span data-ttu-id="0f865-152">編譯的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-152">Compiled Xaml</span></span>  
 <span data-ttu-id="0f865-153">編譯為型別的 XAML 工作流程支援 C# 運算式，當做部分以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 為目標的 C# 工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="0f865-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="0f865-154">編譯的 XAML 是 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 的預設工作流程撰寫型別，而在 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 中所建立的 C# 工作流程專案以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 為目標，並使用 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-154">Compiled XAML is the default type of workflow authoring in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and C# workflow projects created in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <a name="LooseXaml"></a><span data-ttu-id="0f865-155">鬆散的 Xaml</span><span class="sxs-lookup"><span data-stu-id="0f865-155">Loose Xaml</span></span>  
 <span data-ttu-id="0f865-156">鬆散的 XAML 工作流程支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="0f865-157">載入及叫用鬆散的 XAML 工作流程所用之工作流程主機程式，必須以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 為目標，且 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 必須設定為 `true` (預設值為 `false`)。</span><span class="sxs-lookup"><span data-stu-id="0f865-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="0f865-158">若要將 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 設定為 `true`，請建立 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> 執行個體並將其 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 屬性設定為 `true`，然後當做參數傳給 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0f865-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f865-159">如果`CompileExpressions`未設定為`true`、<xref:System.NotSupportedException>就會擲回類似下面的訊息： `Expression Activity type 'CSharpValue`1' 需要編譯才能執行。</span><span class="sxs-lookup"><span data-stu-id="0f865-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="0f865-160">請確定已編譯工作流程。 '</span><span class="sxs-lookup"><span data-stu-id="0f865-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0f865-161">使用 XAML 工作流程，請參閱 <<c2> [ 序列化工作流程和活動 xaml](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="0f865-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <a name="WFServices"></a><span data-ttu-id="0f865-162">在 XAMLX 工作流程服務中使用 C# 運算式</span><span class="sxs-lookup"><span data-stu-id="0f865-162">Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="0f865-163">XAMLX 工作流程服務支援 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="0f865-164">如果工作流程服務是以 IIS 或 WAS 裝載，則不需要其他步驟；但是，如果 XAML 工作流程服務為自我裝載，則必須編譯 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f865-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="0f865-165">若要編譯的自我裝載的 XAMLX 工作流程服務中的 C# 運算式，第一次載入 XAMLX 檔案到`WorkflowService`，然後將傳遞`Body`的`WorkflowService`來`CompileExpressions`中先前所述方法[使用 C#程式碼工作流程中的運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)> 一節。</span><span class="sxs-lookup"><span data-stu-id="0f865-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="0f865-166">下列範例將載入 XAMLX 工作流程服務、編譯 C# 運算式，然後開啟工作流程服務並等候要求。</span><span class="sxs-lookup"><span data-stu-id="0f865-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
```csharp  
// Load the XAMLX workflow service.  
WorkflowService workflow1 =  
    (WorkflowService)XamlServices.Load(xamlxPath);  
  
// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.  
CompileExpressions(workflow1.Body);  
  
// Initialize the WorkflowServiceHost.  
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));  
  
// Enable Metadata publishing/  
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
smb.HttpGetEnabled = true;  
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;  
host.Description.Behaviors.Add(smb);  
  
// Open the WorkflowServiceHost and wait for requests.  
host.Open();  
Console.WriteLine("Press enter to quit");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="0f865-167">如果未編譯 C# 運算式，`Open` 作業會成功，但工作流程在叫用時會失敗。</span><span class="sxs-lookup"><span data-stu-id="0f865-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="0f865-168">下列`CompileExpressions`方法是從先前的方法相同[程式碼工作流程中的使用 C# 運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)> 一節。</span><span class="sxs-lookup"><span data-stu-id="0f865-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```
