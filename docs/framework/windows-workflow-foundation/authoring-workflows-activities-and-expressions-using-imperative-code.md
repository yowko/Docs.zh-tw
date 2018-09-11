---
title: 使用命令式程式碼撰寫工作流程、活動和運算式
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: a0566e01d5786c955562ef97d6d083d886278293
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265126"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>使用命令式程式碼撰寫工作流程、活動和運算式
工作流程定義是配置之活動物件的樹狀。 有很多方式可定義這個活動的樹狀結構，包含手動編輯 XAML 或使用工作流程設計工具來產生 XAML。 不過，XAML 並非必要條件。 您也可以程式設計的方式建立工作流程定義。 本主題提供使用程式碼來建立工作流程定義、活動和運算式的概觀。 如需有關使用程式碼的 XAML 工作流程的範例，請參閱[序列化工作流程和活動與 XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)。  
  
## <a name="creating-workflow-definitions"></a>建立工作流程定義  
 具現化活動型別的執行個體，並設定活動物件的屬性，即可建立工作流程定義。 對於不包含任何子活動的活動，這個部分僅需使用幾行程式碼便能完成。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  本主題中的範例使用 <xref:System.Activities.WorkflowInvoker> 來執行範例工作流程。 如需有關如何叫用工作流程、 傳遞引數，以及可用的不同裝載選項的詳細資訊，請參閱 <<c0> [ 使用 WorkflowInvoker 與 WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)。  
  
 在這個範例中，會建立由單一 <xref:System.Activities.Statements.WriteLine> 活動構成的工作流程。 <xref:System.Activities.Statements.WriteLine> 活動的 <xref:System.Activities.Statements.WriteLine.Text%2A> 引數會進行設定，並叫用工作流程。 如果活動包含子活動，則建構方式會相當類似。 下列範例會使用包含兩個 <xref:System.Activities.Statements.Sequence> 活動的 <xref:System.Activities.Statements.WriteLine> 活動。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>使用物件初始設定式  
 本主題的範例會使用物件初始化語法。 物件初始化語法在使用程式碼建立工作流程定義時會很有用，因為它會在工作流程中提供活動的階層式檢視，並顯示活動之間的關係。 當您以程式設計方式來建立工作流程時，不一定非得使用物件初始化語法。 下列範例在功能上等同於先前的範例。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 如需物件初始設定式的詳細資訊，請參閱[如何： 初始化物件但不呼叫建構函式 （C# 程式設計手冊）](https://go.microsoft.com/fwlink/?LinkId=161015)並[如何： 使用物件初始設定式宣告物件](https://go.microsoft.com/fwlink/?LinkId=161016)。  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>處理變數、常值和運算式  
 使用程式碼建立工作流程定義時，請注意哪個程式碼是做為建立工作流程定義的一部分，以及哪個程式碼是做為該工作流程執行個體的一部分執行。 例如，下列工作流程目的是要產生隨機號碼，並將它寫入主控台。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 當執行此工作流程定義程式碼時，會呼叫 `Random.Next`，且會將結果儲存於工作流程定義做為常值。 此工作流程的許多執行個體都可加以叫用，且所有的執行個體都會顯示相同的號碼。 若要在工作流程執行期間產生隨機號碼，必須使用每當工作流程執行時所計算的運算式。 在下列範例中，會將 Visual Basic 運算式與 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 搭配使用。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 前面範例中的運算式也可以使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 和 C# 運算式實作。  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C# 運算式必須先編譯，才能叫用在包含該 C# 運算式的工作流程。 如果未編譯 C# 運算式，<xref:System.NotSupportedException>時，使用類似下列的訊息叫用工作流程時擲回： `Expression Activity type 'CSharpValue`1' 需要編譯才能執行。  請確定已編譯工作流程。 ' 在大部分情況下，涉及在 Visual Studio C# 中建立的工作流程運算式，都會自動編譯，但在某些情況下，程式碼工作流程，例如 C# 運算式必須以手動方式編譯。 如需如何編譯 C# 運算式的範例，請參閱 <<c0> [ 程式碼工作流程中的使用 C# 運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)一節[C# 運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)主題。  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 是以 Visual Basic 語法表示的運算式，可用來當做運算式中的右值 (r-value)，而 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 是以 C# 語法表示的運算式，可用來當做運算式中的右值。 每次執行包含的活動時會評估這些運算式。 運算式的結果會指派至工作流程變數 `n`，且會由工作流程中的下一個活動使用這些結果。 若要在執行階段時存取工作流程變數 `n` 的值，必須要有 <xref:System.Activities.ActivityContext>。 這可以使用下列 Lambda 運算式來進行存取。  
  
> [!NOTE]
>  請注意這兩個程式碼都是使用 C# 做為程式設計語言的範例，但一個是使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>，另一個則是使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601>。 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 可以用在 Visual Basic 和 C# 專案中。 根據預設，在工作流程設計工具中所建立的運算式符合裝載專案的語言。 以程式碼建立工作流程時，由工作流程作者自行決定要使用的語言。  
  
 在這些範例中，運算式的結果會指派至工作流程變數 `n`，且會由工作流程中的下一個活動使用這些結果。 若要在執行階段時存取工作流程變數 `n` 的值，必須要有 <xref:System.Activities.ActivityContext>。 這可以使用下列 Lambda 運算式來進行存取。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 如需有關 lambda 運算式的詳細資訊，請參閱[Lambda 運算式 （C# 程式設計指南）](https://go.microsoft.com/fwlink/?LinkID=152436)或是[Lambda 運算式 (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437)。  
  
 Lambda 運算式不可序列化為 XAML 格式。 如果嘗試序列化內含 Lambda 運算式的工作流程，會擲回 <xref:System.Activities.Expressions.LambdaSerializationException> 和下列訊息：「此工作流程包含程式碼中指定的 Lambda 運算式。 這些運算式並非 XAML 可序列化。 若要讓您的工作流程成為 XAML 可序列化，請使用 VisualBasicValue/VisualBasicReference 或 ExpressionServices.Convert(lambda)。 這會將您的 Lambda 運算式轉換成運算式活動。」 若要讓此運算式相容於 XAML，請使用 <xref:System.Activities.Expressions.ExpressionServices> 與 <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>，如下列範例所示。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 也可以使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>。 請注意，使用 Visual Basic 運算式時，不需要 Lambda 運算式。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Visual Basic 運算式會在執行階段編譯成 LINQ 運算式。 前面兩個範例都可序列化為 XAML，但是如果已序列化的 XAML 是要在工作流程設計工具中檢視和編輯，則在運算式使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>。 使用 `ExpressionServices.Convert` 的序列化工作流程可在設計工具中開啟，但運算式的值會是空白的。 如需序列化 XAML 工作流程的詳細資訊，請參閱[序列化工作流程和活動與 XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)。  
  
#### <a name="literal-expressions-and-reference-types"></a>常值運算式及參考類型  
 常值運算式在工作流程中由 <xref:System.Activities.Expressions.Literal%601> 活動表示。 下列 <xref:System.Activities.Statements.WriteLine> 活動的功能相同。  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 初始化含任何參考類型 (<xref:System.String> 除外) 的常值運算式皆無效。 在下列範例中，<xref:System.Activities.Statements.Assign> 活動的 <xref:System.Activities.Statements.Assign.Value%2A> 屬性是以使用 `List<string>` 的常值運算式初始化。  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 當驗證內含此活動的工作流程時，會傳回下列驗證錯誤：「常值只支援值型別和不可變型別 System.String。 System.Collections.Generic.List`1[System.String] 型別不能用做常值。」 如果叫用工作流程，會擲回 <xref:System.Activities.InvalidWorkflowException>，其中包含驗證錯誤的文字。 這是驗證錯誤，因為建立內含參考類型的常值運算式，並不會針對工作流程的每個執行個體建立新的參考類型執行個體。 若要解決此問題，請將常值運算式換成可以建立和傳回新參考類型執行個體的運算式。  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 如需有關運算式的詳細資訊，請參閱 <<c0> [ 運算式](../../../docs/framework/windows-workflow-foundation/expressions.md)。  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>在物件上使用運算式和 InvokeMethod 活動的叫用方法  
 <xref:System.Activities.Expressions.InvokeMethod%601> 活動可以用來在 .NET Framework 中叫用類別的靜態和執行個體方法。 在本主題先前的範例中，已使用 <xref:System.Random> 類別來產生隨機數字。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> 活動也可以用來呼叫 <xref:System.Random.Next%2A> 類別的 <xref:System.Random> 方法。  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =   
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 由於 <xref:System.Random.Next%2A> 不是靜態方法，因此會提供 <xref:System.Random> 類別的執行個體給 <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> 屬性。 在此範例中，會使用 Visual Basic 運算式建立新執行個體，但是該執行個體也可能已建立並儲存在工作流程變數中。 在此範例中，使用 <xref:System.Activities.Statements.Assign%601> 活動而不是 <xref:System.Activities.Expressions.InvokeMethod%601> 活動會比較簡單。 如果最終由 <xref:System.Activities.Statements.Assign%601> 或 <xref:System.Activities.Expressions.InvokeMethod%601> 活動叫用的方法呼叫為長期執行，則 <xref:System.Activities.Expressions.InvokeMethod%601> 具有優勢，因為它有 <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> 屬性。 當此屬性設為 `true` 時，叫用的方法會以非同步方式執行 (與工作流程有關)。 如果有其他活動平行，當方法以非同步方式執行時，那些活動不會被封鎖。 此外，如果所要叫用的方法沒有傳回值，那麼 <xref:System.Activities.Expressions.InvokeMethod%601> 會是叫用方法的適當方式。  
  
## <a name="arguments-and-dynamic-activities"></a>引數與動態活動  
 工作流程定義是藉由將活動組裝在活動樹狀目錄中，並設定任何屬性與引數，而建立在程式碼中。 可繫結現有的引數，但無法新增新引數至活動。 這包含傳遞至根活動的工作流程引數。 在命令式程式碼中，會將工作流程引數指定為新 CLR 型別的屬性，並且在 XAML 中使用 `x:Class` 與 `x:Member` 來宣告它們。 因為將工作流程定義建立為記憶體內物件的樹狀結構時，並未建立任何新 CLR 型別，所以無法新增引數。 但是，可新增引數至 <xref:System.Activities.DynamicActivity>。 在此範例中會建立 <xref:System.Activities.DynamicActivity%601>，它採用兩個整數引數並將其同時加入，然後傳回結果。 不僅會針對每個引數建立 <xref:System.Activities.DynamicActivityProperty>，且會將作業的結果指派至 <xref:System.Activities.Activity%601.Result%2A> 的 <xref:System.Activities.DynamicActivity%601> 引數。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 如需有關動態活動的詳細資訊，請參閱[在執行階段建立活動](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)。  
  
## <a name="compiled-activities"></a>已編譯的活動  
 動態活動是使用程式碼來定義包含引數之活動的一種方法，但活動也可以用程式碼建立，並編譯成型別。 可以建立衍生自 <xref:System.Activities.CodeActivity> 的簡單活動，以及衍生自 <xref:System.Activities.AsyncCodeActivity> 的非同步活動。 這些活動可以具有引數、傳回值，並使用命令式程式碼定義其邏輯。 如需建立這些類型的活動的範例，請參閱[CodeActivity 基底類別](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md)並[建立非同步活動](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)。  
  
 衍生自 <xref:System.Activities.NativeActivity> 的活動可以使用命令式程式碼來定義其邏輯，而且也可以包含定義邏輯的子活動。 這些活動也可以完整存取執行階段的功能，例如建立書籤。 針對建立的範例<xref:System.Activities.NativeActivity>-基底活動，請參閱[NativeActivity 基底類別](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md)， [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)，和[自訂複合使用原生活動](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)範例。  
  
 衍生自 <xref:System.Activities.Activity> 的活動可以藉由使用子活動，只定義其邏輯。 這些活動通常是使用工作流程設計工具來建立，但也可以使用程式碼來定義。 在下列範例中，會定義衍生自 `Square` 的 `Activity<int>` 活動。 `Square` 活動具有名為 <xref:System.Activities.InArgument%601> 的單一 `Value`，並使用 <xref:System.Activities.Statements.Sequence> 屬性來指定 <xref:System.Activities.Activity.Implementation%2A> 活動，以定義其邏輯。 <xref:System.Activities.Statements.Sequence> 活動包含 <xref:System.Activities.Statements.WriteLine> 活動和 <xref:System.Activities.Statements.Assign%601> 活動。 這三個活動在一起可實作 `Square` 活動的邏輯。  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 在下列範例中，會使用 `Square` 來叫用由單一 <xref:System.Activities.WorkflowInvoker> 活動組成的工作流程定義。  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 當叫用此工作流程時，主控台會顯示下列輸出：  
  
 **Number 值： 5**  
**結果： 25**
