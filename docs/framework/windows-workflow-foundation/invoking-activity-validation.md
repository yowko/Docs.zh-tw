---
title: 叫用活動驗證
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c334c13457b3e89e451f75e1ca9ea9e00aae1e21
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="invoking-activity-validation"></a>叫用活動驗證
活動驗證提供的方法可在活動執行前識別及報告任何活動之組態中的錯誤。 在工作流程設計工具中修改工作流程時，若工作流程設計工具中顯示任何驗證錯誤或警告，就會進行驗證。 叫用工作流程時，也會在執行階段進行驗證，而且如果發生任何驗證錯誤，預設驗證邏輯會擲回 <xref:System.Activities.InvalidWorkflowException>。 Windows Workflow Foundation (WF) 提供<xref:System.Activities.Validation.ActivityValidationServices>可以由工作流程應用程式和工具開發人員用來明確驗證活動的類別。 本主題描述如何使用 <xref:System.Activities.Validation.ActivityValidationServices> 執行活動驗證。  
  
## <a name="using-activityvalidationservices"></a>使用 ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices> 具有兩個 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 負載，可用於叫用活動的驗證邏輯。 第一個多載會採用要驗證的根活動，然後傳回驗證錯誤及警告的集合。 下列範例中會使用具有兩個必要引數的自訂 `Add` 活動。  
  
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
  
 `Add` 活動用於 <xref:System.Activities.Statements.Sequence> 內部，但其兩個必要的引數並未繫結，如下列範例所示。  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 您可以呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 來驗證此工作流程。 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 會傳回活動和任何子活動中包含的任何驗證錯誤或警告集合，如下列範例所示。  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 在此工作流程範例中呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 時，會傳回兩個驗證錯誤。  
  
 **錯誤： 未提供必要的活動引數 'Operand2' 的值。**  
**錯誤： 未提供必要的活動引數 'Operand1' 的值。**  如果叫用這個工作流程，就會擲回 <xref:System.Activities.InvalidWorkflowException>，如下列範例所示。  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 **System.Activities.InvalidWorkflowException:**  
**處理工作流程樹狀結構時發生下列錯誤：**   
**'Add': 未提供必要的活動引數 'Operand2' 的值。**   
**'Add': 未提供必要的活動引數 'Operand1' 的值。**  若要讓這個工作流程範例生效，就必須繫結 `Add` 活動的兩個必要引數。 在下列範例中，兩個必要引數會與結果值一同繫結於工作流程變數。 在此範例中，<xref:System.Activities.Activity%601.Result%2A> 引數會與兩個必要的引數一同繫結。 <xref:System.Activities.Activity%601.Result%2A> 引數不需繫結，若不繫結此引數，也不會導致驗證錯誤。 如果工作流程中的其他位置會使用 <xref:System.Activities.Activity%601.Result%2A> 的值，工作流程作者必須負責繫結該值。  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>在根活動驗證必要的引數  
 如果工作流程的根活動含有引數，則在叫用該工作流程並將參數傳遞到該工作流程之前，這些都不會被繫結。 下列工作流程會通過驗證，但若叫用工作流程而未傳入必要的引數，則會擲回例外狀況，如下列範例所示。  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 **System.ArgumentException： 根活動之引數設定不正確。**  
**請修正工作流程定義，或提供輸入的值來修正這些錯誤：**   
**'Add': 未提供必要的活動引數 'Operand2' 的值。**   
**'Add': 未提供必要的活動引數 'Operand1' 的值。**  傳遞正確的引數後，工作流程就會成功完成，如下列範例所示。  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
>  在此範例中，根活動會宣告為 `Add`，而非上一個範例中的 `Activity`。 這樣可讓 `WorkflowInvoker.Invoke` 方法傳回單一整數，代表 `Add` 活動的結果 (而非 `out` 引數的字典)。 變數 `wf` 也可能已宣告為 `Activity<int>`。  
  
 驗證根引數時，主機應用程式必須負責確保叫用工作流程時，會傳遞所有必要的引數。  
  
### <a name="invoking-imperative-code-based-validation"></a>叫用命令式的程式碼式驗證  
 命令式的程式碼驗證提供一個簡單的方式，可讓活動提供與其本身相關的驗證，而且適用於衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動。 活動中會加入用來判斷任何驗證錯誤或警告的驗證程式碼。 在活動叫用驗證時，這些警告或錯誤包含在呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 所傳回的集合中。 在下列範例中，取自[基本驗證](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md)範例中，`CreateProduct`活動定義。 如果 `Cost` 大於 `Price`，就會將驗證錯誤加入至<xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中的中繼資料。  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 在此範例中，會使用 `CreateProduct` 活動來設定工作流程。 在此工作流程中，`Cost` 大於 `Price`，而且未設定必要的 `Description` 引數。 叫用驗證時，會傳回下列錯誤。  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =   
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 **錯誤： 成本必須小於或等於價格。**  
**錯誤： 未提供必要的活動引數 'Description' 的值。**    
> [!NOTE]
>  自訂活動作者可以在活動的 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中提供驗證邏輯。 從 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 擲回的任何例外狀況都不會被視為驗證錯誤。 這些例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中逸出，而且必須由呼叫端處理。  
  
## <a name="using-validationsettings"></a>使用 ValidationSettings  
 根據預設，當 <xref:System.Activities.Validation.ActivityValidationServices> 叫用驗證時，會評估活動樹狀結構中的所有活動。 <xref:System.Activities.Validation.ValidationSettings> 允許透過設定驗證的三個屬性，以數種不同的方式自訂驗證。 <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 指定驗證程式是否應逐一查核整個活動樹狀結構，或者只需將驗證邏輯套用於所提供的活動。 此值的預設值為 `false`。 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 會指定從型別至條件約束清單的其他條件約束對應。 為取得要驗證之活動樹狀結構中每個活動的基底型別，會查詢 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>。 如果找到相符的條件約束清單，會為該活動評估清單中的所有條件約束。 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 指定驗證程式是否應評估所有條件約束，或者只需評估 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 中指定的條件約束。 預設值是 `false`。 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>和 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 適合讓工作流程主機作者用來新增額外的工作流程驗證，例如 FxCop 等工具的原則條件約束。 如需條件約束的詳細資訊，請參閱[宣告式條件約束](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)。  
  
 若要使用 <xref:System.Activities.Validation.ValidationSettings>，請設定所需的屬性，然後在對 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中傳遞它。 在此範例中，會驗證包含 <xref:System.Activities.Statements.Sequence> 的活動 (該活動具有 `Add` 活動)。 `Add` 活動具有兩個必要引數。  
  
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
  
 `Add` 中會使用下列 <xref:System.Activities.Statements.Sequence> 活動，但不會繫結其兩個必要的引數。  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 針對下列範例，驗證執行時，<xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 會設定為 `true`，因此只會驗證根 <xref:System.Activities.Statements.Sequence> 活動。  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 這個程式碼會顯示下列輸出：  
  
 **沒有警告或錯誤**即使`Add`活動具有必要引數未繫結中，驗證會成功，因為會評估根活動。 若只驗證活動樹狀中的特定項目，例如要在設計工具中驗證單一活動的屬性變更，這種類型的驗證相當有用。 請注意，若叫用此工作流程，會評估工作流程中設定的完整驗證，而且可能會擲回 <xref:System.Activities.InvalidWorkflowException>。 <xref:System.Activities.Validation.ActivityValidationServices> 和 <xref:System.Activities.Validation.ValidationSettings> 只會設定主機明確叫用的驗證，不會設定叫用工作流程時所發生的驗證。
