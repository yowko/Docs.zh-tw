---
title: C# 運算式
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: b0e5d7f2fbb1f7b84c6d8f0110bd111165f0ea52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239610"
---
# <a name="c-expressions"></a>C# 運算式

從 .NET Framework 4.5 開始，Windows Workflow Foundation (WF) 都支援 c # 運算式。 新的 c # 工作流程專案是在 Visual Studio 2012 中建立，其目標為 .NET Framework 4.5 使用 c # 運算式，而 Visual Basic 工作流程專案則使用 Visual Basic 的運算式。 使用 Visual Basic 運算式的現有 .NET Framework 4 個工作流程專案， [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 不論專案語言為何，都可以遷移至其中。 本主題提供 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的 C# 運算式概觀。

## <a name="using-c-expressions-in-workflows"></a>在工作流程中使用 C# 運算式

- [在工作流程設計工具中使用 C# 運算式](csharp-expressions.md#WFDesigner)

  - [回溯相容性](csharp-expressions.md#BackwardCompat)

- [在程式碼工作流程中使用 C# 運算式](csharp-expressions.md#CodeWorkflows)

- [在 XAML 工作流程中使用 C# 運算式](csharp-expressions.md#XamlWorkflows)

  - [編譯的 XAML](csharp-expressions.md#CompiledXaml)

  - [鬆散的 Xaml](csharp-expressions.md#LooseXaml)

- [在 XAMLX 工作流程服務中使用 C# 運算式](csharp-expressions.md#WFServices)

### <a name="using-c-expressions-in-the-workflow-designer"></a><a name="WFDesigner"></a> 在工作流程設計工具中使用 c # 運算式

從 .NET Framework 4.5 開始，Windows Workflow Foundation (WF) 都支援 c # 運算式。 在 Visual Studio 2012 中建立的 c # 工作流程專案，以 .NET Framework 4.5 使用 c # 運算式，而 Visual Basic 工作流程專案則使用 Visual Basic 的運算式。 若要指定所需的 c # 運算式，請在標示為 [ **輸入 c # 運算式**] 的方塊中輸入。 在設計工具中選取活動時，會在屬性視窗中顯示此標籤，而此標籤也會顯示在工作流程設計工具中的活動之上。 在下列範例中，`WriteLine` 內的 `Sequence` 包含兩個 `NoPersistScope` 活動。

![顯示自動建立之序列活動的螢幕擷取畫面。](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> C # 運算式僅在 Visual Studio 中受到支援，而且在重新裝載的工作流程設計工具中不支援。 如需重新裝載設計工具所支援的新 WF45 功能的詳細資訊，請參閱 [重新裝載工作流程設計工具中的新 Workflow Foundation 4.5 功能支援](wf-features-in-the-rehosted-workflow-designer.md)。

#### <a name="backwards-compatibility"></a><a name="BackwardCompat"></a> 回溯相容性

支援現有 .NET Framework 4 c # 工作流程專案中已遷移至的 Visual Basic 運算式 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 。 在工作流程設計工具中查看 Visual Basic 運算式時，除非 Visual Basic 運算式是有效的 c # 語法，否則現有 Visual Basic 運算式的文字會取代為 **在 XAML 中設定的值**。 如果 Visual Basic 運算式為有效的 C# 語法，則會顯示該運算式。 若要將 Visual Basic 運算式更新為 C#，您可以在工作流程設計工具中編輯這些運算式，並指定相等的 C# 運算式。 您不需要將 Visual Basic 運算式更新為 C#，不過一旦這些運算式在工作流程設計工具中更新，將會轉換為 C#，且可能無法還原為 Visual Basic。

### <a name="using-c-expressions-in-code-workflows"></a><a name="CodeWorkflows"></a> 在程式碼工作流程中使用 c # 運算式

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 程式碼為主的工作流程支援 C# 運算式，但是您必須使用 <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> 編譯 C# 運算式，工作流程才能叫用運算式。 工作流程作者可以使用 `CSharpValue` 來表示運算式的右值 (r-value)，並使用 `CSharpReference` 來表示運算式的左值 (l-value)。 下列範例使用 `Assign` 活動內含的 `WriteLine` 活動和 `Sequence` 活動，來建立工作流程。 該範例為 `CSharpReference` 的 `To` 引數，指定一個 `Assign`，表示運算式的左值。 `CSharpValue` 的 `Value` 引數和 `Assign` 的 `Text` 引數指定一個 `WriteLine`，表示這兩個運算式的右值。

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

建構工作流程之後，會呼叫 `CompileExpressions` Helper 方法來編譯 C# 運算式，然後叫用工作流程。 以下範例是 `CompileExpressions` 方法。

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
> 如果未編譯 c # 運算式，則 <xref:System.NotSupportedException> 會在使用類似下列的訊息來叫用工作流程時擲回： `Expression Activity type 'CSharpValue` 1 ' 需要編譯才能執行。  請確定已編譯工作流程。

如果您的自訂程式碼為主之工作流程使用 `DynamicActivity`，則需要對 `CompileExpressions` 方法進行一些變更，如下列程式碼範例所示。

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

在動態活動中編譯 C# 運算式的 `CompileExpressions` 多載有一些差異。

- 傳給 `CompileExpressions` 的參數為 `DynamicActivity`。

- 擷取型別名稱和命名空間需使用 `DynamicActivity.Name` 屬性。

- `TextExpressionCompilerSettings.ForImplementation` 設定為 `true`。

- 呼叫 `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`，而不是 `CompiledExpressionInvoker.SetCompiledExpressionRoot`。

如需在程式碼中使用運算式的詳細資訊，請參閱 [使用命令式程式碼撰寫工作流程、活動和運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。

### <a name="using-c-expressions-in-xaml-workflows"></a><a name="XamlWorkflows"></a> 在 XAML 工作流程中使用 c # 運算式

XAML 工作流程支援 C# 運算式。 編譯的 XAML 工作流程會編譯為型別，而鬆散的 XAML 工作流程會在工作流程執行時，由執行階段載入並編譯為活動樹狀。

- [編譯的 XAML](csharp-expressions.md#CompiledXaml)

- [鬆散的 Xaml](csharp-expressions.md#LooseXaml)

#### <a name="compiled-xaml"></a><a name="CompiledXaml"></a> 編譯的 Xaml

編譯為型別的 XAML 工作流程支援 C# 運算式，當做部分以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 為目標的 C# 工作流程專案。 編譯的 XAML 是 Visual Studio 中的工作流程撰寫的預設類型，而在以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 使用 c # 運算式的 Visual Studio 中建立的 c # 工作流程專案。

#### <a name="loose-xaml"></a><a name="LooseXaml"></a> 鬆散的 Xaml

鬆散的 XAML 工作流程支援 C# 運算式。 載入及叫用鬆散的 XAML 工作流程所用之工作流程主機程式，必須以 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 為目標，且 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 必須設定為 `true` (預設值為 `false`)。 若要將 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 設定為 `true`，請建立 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> 執行個體並將其 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> 屬性設定為 `true`，然後當做參數傳給 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>。 如果未 `CompileExpressions` 設定為，則會擲回 `true` ， <xref:System.NotSupportedException> 並出現類似下列的訊息： `Expression Activity type 'CSharpValue` 1 ' 需要編譯才能執行。  請確定已編譯工作流程。

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

如需使用 XAML 工作流程的詳細資訊，請參閱 [從 xaml 序列化工作流程和活動](serializing-workflows-and-activities-to-and-from-xaml.md)。

### <a name="using-c-expressions-in-xamlx-workflow-services"></a><a name="WFServices"></a> 在 SERVICE1.XAMLX 工作流程服務中使用 c # 運算式

XAMLX 工作流程服務支援 C# 運算式。 如果工作流程服務是以 IIS 或 WAS 裝載，則不需要其他步驟；但是，如果 XAML 工作流程服務為自我裝載，則必須編譯 C# 運算式。 若要在自我裝載的 SERVICE1.XAMLX 工作流程服務中編譯 c # 運算式，請先將 SERVICE1.XAMLX 檔案載入，然後將的 `WorkflowService` 傳遞 `Body` 至先前在程式 `WorkflowService` `CompileExpressions` [代碼工作流程中使用 c # 運算式](csharp-expressions.md#CodeWorkflows) 一節所述的方法。 下列範例將載入 XAMLX 工作流程服務、編譯 C# 運算式，然後開啟工作流程服務並等候要求。

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

如果未編譯 C# 運算式，`Open` 作業會成功，但工作流程在叫用時會失敗。 下列 `CompileExpressions` 方法與上一節 [在程式碼工作流程中使用 c # 運算式](csharp-expressions.md#CodeWorkflows) 的方法相同。

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
