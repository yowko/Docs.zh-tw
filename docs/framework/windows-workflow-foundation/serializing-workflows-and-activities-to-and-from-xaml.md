---
title: 序列化工作流程及 XAML 之間的活動
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: c18afa7232adabc4f1c4e17fde993064b9189e39
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671900"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="0439e-102">將工作流程和活動序列化為 XAML</span><span class="sxs-lookup"><span data-stu-id="0439e-102">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="0439e-103">除了將工作流程定義編譯成包含在組件中的類型之外，工作流程定義也可以序列化為 XAML。</span><span class="sxs-lookup"><span data-stu-id="0439e-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="0439e-104">這些序列化的定義可重新載入以供編輯或檢閱、傳遞至建置系統以進行編譯，或載入及叫用。</span><span class="sxs-lookup"><span data-stu-id="0439e-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="0439e-105">本主題提供序列化工作流程定義以及使用 XAML 工作流程定義的概觀。</span><span class="sxs-lookup"><span data-stu-id="0439e-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="0439e-106">使用 XAML 工作流程定義</span><span class="sxs-lookup"><span data-stu-id="0439e-106">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="0439e-107">若要建立要序列化的工作流程定義，請使用 <xref:System.Activities.ActivityBuilder> 類別。</span><span class="sxs-lookup"><span data-stu-id="0439e-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="0439e-108">建立 <xref:System.Activities.ActivityBuilder> 與建立 <xref:System.Activities.DynamicActivity> 十分類似。</span><span class="sxs-lookup"><span data-stu-id="0439e-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="0439e-109">您要指定任何所需的引數，以及設定構成行為的活動。</span><span class="sxs-lookup"><span data-stu-id="0439e-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="0439e-110">在下列範例中，會建立 `Add` 活動，它接受兩個輸入引數、加總這些引數，然後傳回結果。</span><span class="sxs-lookup"><span data-stu-id="0439e-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="0439e-111">因為這個活動會傳回結果，所以要使用泛型 <xref:System.Activities.ActivityBuilder%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="0439e-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="0439e-112">每個 <xref:System.Activities.DynamicActivityProperty> 執行個體代表工作流程的一個輸入引數，而 <xref:System.Activities.ActivityBuilder.Implementation%2A> 包含形成工作流程邏輯的活動。</span><span class="sxs-lookup"><span data-stu-id="0439e-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="0439e-113">請注意，此範例中的右值 (r-value) 運算式是 Visual Basic 運算式。</span><span class="sxs-lookup"><span data-stu-id="0439e-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="0439e-114">Lambda 運算式不可序列化成 XAML，除非使用 <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>。</span><span class="sxs-lookup"><span data-stu-id="0439e-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="0439e-115">如果要在工作流程設計工具中開啟或編輯序列化的工作流程, 則應該使用 Visual Basic 運算式。</span><span class="sxs-lookup"><span data-stu-id="0439e-115">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="0439e-116">如需詳細資訊, 請參閱[使用命令式程式碼撰寫工作流程、活動和運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="0439e-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="0439e-117">若要將 <xref:System.Activities.ActivityBuilder> 執行個體代表的工作流程定義序列化為 XAML，請使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices> 建立 <xref:System.Xaml.XamlWriter>，然後使用 <xref:System.Xaml.XamlServices> 將工作流程定義序列化 (使用 <xref:System.Xaml.XamlWriter>)。</span><span class="sxs-lookup"><span data-stu-id="0439e-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="0439e-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices>有方法可將<xref:System.Activities.ActivityBuilder>實例對應至 xaml, 以及載入 xaml 工作流程, 並傳回<xref:System.Activities.DynamicActivity>可叫用的。</span><span class="sxs-lookup"><span data-stu-id="0439e-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="0439e-119">在下列範例中, 上<xref:System.Activities.ActivityBuilder>一個範例中的實例會序列化為字串, 並儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="0439e-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="0439e-120">下列範例代表序列化的工作流程。</span><span class="sxs-lookup"><span data-stu-id="0439e-120">The following example represents the serialized workflow.</span></span>

```xaml
<Activity
  x:TypeArguments="x:Int32"
  x:Class="Add"
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />
  </x:Members>
  <Sequence>
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">
      <Assign.To>
        <OutArgument x:TypeArguments="x:Int32">
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />
          </OutArgument>
      </Assign.To>
    </Assign>
  </Sequence>
</Activity>
```

<span data-ttu-id="0439e-121">若要載入序列化的工作流程, <xref:System.Activities.XamlIntegration.ActivityXamlServices>請使用<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0439e-121">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="0439e-122">這個方法接受序列化的工作流程定義，並傳回代表工作流程定義的 <xref:System.Activities.DynamicActivity>。</span><span class="sxs-lookup"><span data-stu-id="0439e-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="0439e-123">請注意，等到驗證程序期間呼叫 <xref:System.Activities.Activity.CacheMetadata%2A> 主體上的 <xref:System.Activities.DynamicActivity> 時，XAML 才會還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0439e-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="0439e-124">如果未明確呼叫驗證, 則會在叫用工作流程時執行。</span><span class="sxs-lookup"><span data-stu-id="0439e-124">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="0439e-125">如果 XAML 工作流程定義無效，則會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0439e-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="0439e-126">從 <xref:System.Activities.Activity.CacheMetadata%2A> 擲回的任何例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 呼叫中逸出，而且必須由呼叫端處理。</span><span class="sxs-lookup"><span data-stu-id="0439e-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="0439e-127">在下列範例中，會載入上一個範例的序列化工作流程，並透過 <xref:System.Activities.WorkflowInvoker> 叫用它。</span><span class="sxs-lookup"><span data-stu-id="0439e-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="0439e-128">當叫用這個工作流程時，主控台就會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="0439e-128">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="0439e-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="0439e-129">**25 + 15**</span></span>\
<span data-ttu-id="0439e-130">**40**</span><span class="sxs-lookup"><span data-stu-id="0439e-130">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="0439e-131">如需使用輸入和輸出引數叫用工作流程的詳細資訊, 請參閱<xref:System.Activities.WorkflowInvoker.Invoke%2A>[使用 WorkflowInvoker 和 WorkflowApplication](using-workflowinvoker-and-workflowapplication.md)和。</span><span class="sxs-lookup"><span data-stu-id="0439e-131">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="0439e-132">如果序列化的工作流程C#包含運算式, 則<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings>將其屬性<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A>設為`true`的實例<xref:System.NotSupportedException>必須當做參數傳遞至<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, 否則將會擲回, 並顯示類似的訊息如下所示:**運算式活動類型 ' CSharpValue ' 1 ' 需要編譯, 才能執行。請確定已編譯工作流程。**</span><span class="sxs-lookup"><span data-stu-id="0439e-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="0439e-133">如需詳細資訊, 請參閱[ C#運算式](csharp-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0439e-133">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="0439e-134">您也可以<xref:System.Activities.ActivityBuilder> <xref:System.Activities.XamlIntegration.ActivityXamlServices>使用方法, 將序列化的工作流程定義載入至實例。 <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A></span><span class="sxs-lookup"><span data-stu-id="0439e-134">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="0439e-135">將序列化的工作流程載入<xref:System.Activities.ActivityBuilder>實例之後, 即可加以檢查和修改。</span><span class="sxs-lookup"><span data-stu-id="0439e-135">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="0439e-136">對自訂工作流程設計工具作者來說，這項功能很實用，在設計過程中提供了儲存及重新載入工作流程定義的機制。</span><span class="sxs-lookup"><span data-stu-id="0439e-136">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="0439e-137">在下列範例中，會載入上一個範例的序列化工作流程定義，並檢查其屬性。</span><span class="sxs-lookup"><span data-stu-id="0439e-137">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
