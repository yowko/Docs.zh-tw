---
title: 變數與引數
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 7d4bcbb28ffac0ea0f2f6d4aa238523855570f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520103"
---
# <a name="variables-and-arguments"></a>變數與引數
在 Windows Workflow Foundation (WF) 中，變數表示資料的儲存體，而引數表示資料流程傳入活動和從活動。 活動有一組引數，且它們會構成活動的簽章。 此外，活動也包含變數的清單，開發人員可在設計工作流程時加入或移除其中的變數。 引數會使用傳回值的運算式來繫結。  
  
## <a name="variables"></a>變數  
 變數是資料的儲存位置。 變數會宣告為工作流程定義的一部分， 並負責執行階段的值，而這些值會儲存成工作流程執行個體狀態的一部分。 變數定義會指定變數的型別，以及選擇性地指定名稱。 下列程式碼顯示如何使用 <xref:System.Activities.Statements.Assign%601> 活動來宣告變數、將值指派至變數，然後使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台上顯示其值。  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 預設的值運算式可選擇性地指定為變數宣告的一部分。 變數亦可含有修飾詞。 例如，如果變數是唯讀，即可套用 <xref:System.Activities.VariableModifiers> 修飾詞。 在下列範例中，會建立具有指派預設值的唯讀變數。  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>變數範圍  
 執行階段時的變數存留期會等於宣告此變數的活動存留期。 當活動完成時會清除其變數，而且也不可再進行參照。  
  
## <a name="arguments"></a>引數  
 活動作者會使用引數來定義資料流入與流出活動的方式。 每個引數都有指定的方向：<xref:System.Activities.ArgumentDirection.In>、<xref:System.Activities.ArgumentDirection.Out> 或 <xref:System.Activities.ArgumentDirection.InOut>。  
  
 工作流程執行階段會對資料進出活動的時機提供以下保證：  
  
1.  當活動開始執行時，會計算其所有輸入與輸入/輸出引數的值。 例如，不論何時呼叫 <xref:System.Activities.Argument.Get%2A>，傳回的值優先為執行階段所計算的值，然後才是其 `Execute` 的引動值。  
  
2.  當呼叫 <xref:System.Activities.InOutArgument%601.Set%2A> 時，執行階段會立即設定值。  
  
3.  引數可以選擇是否要指定它們的 <xref:System.Activities.Argument.EvaluationOrder%2A>。 <xref:System.Activities.Argument.EvaluationOrder%2A> 是指定評估引數順序之以零為起始的值。 根據預設，引數的預設評估順序未指定，而且等於 <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> 值。 設定 <xref:System.Activities.Argument.EvaluationOrder%2A> 為大於或等於零的值，以指定這個引數的評估順序。 Windows Workflow Foundation 評估引數的指定的評估順序，依遞增順序排列。 請注意，未指定評估順序的引數會在有指定評估順序的引數之前先進行評估。  
  
 活動作者可使用強型別的機制來公開其引數。 藉由宣告型別 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 與 <xref:System.Activities.InOutArgument%601> 的屬性，即可完成此動作。 這可讓活動作者建立資料進出活動的相關特定合約。  
  
### <a name="defining-the-arguments-on-an-activity"></a>定義活動的引數  
 藉由指定型別 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 與 <xref:System.Activities.InOutArgument%601> 的屬性，即可在活動上定義引數。 下列程式碼顯示如何定義帶入字串以顯示使用者，並傳回包含使用者回應字串之 `Prompt` 活動的引數。  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  傳回單一值的活動可衍生自 <xref:System.Activities.Activity%601>、<xref:System.Activities.NativeActivity%601> 或 <xref:System.Activities.CodeActivity%601>。 這些活動具有充分定義的 <xref:System.Activities.OutArgument%601> 具名 <xref:System.Activities.Activity%601.Result%2A>，其中包含活動的傳回值。  
  
### <a name="using-variables-and-arguments-in-workflows"></a>在工作流程中使用變數與引數  
 下列範例示範如何在工作流程中使用變數與引數。 工作流程會依照順序宣告三種變數：`var1`、`var2` 與 `var3`。 工作流程中的第一個活動是指派變數 `Assign` 值到變數 `var1` 的 `var2` 活動。 這之後的 `WriteLine` 活動會列印 `var2` 變數的值。 下一步是指派變數 `Assign` 到變數 `var2` 的其他 `var3` 活動。 最後一步是另一個 `WriteLine` 活動，這個活動會列印 `var3` 變數的值。 第一個 `Assign` 活動會使用明確表示活動引數繫結的 `InArgument<string>` 和 `OutArgument<string>`。 `InArgument<string>` 適用於 <xref:System.Activities.Statements.Assign.Value%2A>，因為該值會透過其 <xref:System.Activities.Statements.Assign%601> 引數流入 <xref:System.Activities.Statements.Assign.Value%2A> 活動中，而 `OutArgument<string>` 適用於 <xref:System.Activities.Statements.Assign.To%2A>，因為該值會從 <xref:System.Activities.Statements.Assign.To%2A> 引數流出到變數中。 第二個 `Assign` 活動會完成同樣的工作，並使用更精簡但使用隱含轉型的對等語法。 `WriteLine` 活動也會使用精簡語法。  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>在程式碼式活動中使用變數與引數  
 先前的範例示範如何在工作流程中使用引數與宣告式活動。 在程式碼式活動中也會使用引數與變數。 概念上，其用法很類似。 變數表示活動內的資料存放區，而引數表示資料對活動的流入或流出，且是由工作流程作者繫結至工作流程中表示資料流出或流入位置的其他變數或引數。 若要取得或設定活動中的變數或引數值，必須使用表示活動目前執行環境的活動內容。 這會由工作流程執行階段傳遞至活動的 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法。 在此範例中，會定義含有兩個 `Add` 引數的自訂 <xref:System.Activities.ArgumentDirection.In> 活動。 若要存取引數值，則會使用 <xref:System.Activities.Argument.Get%2A> 方法，且要使用工作流程執行階段所傳遞的內容。  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 如需有關引數、 變數和運算式程式碼中的使用的詳細資訊，請參閱[撰寫工作流程、 活動和運算式使用命令式程式碼](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)和[所需的引數與多載群組](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).
