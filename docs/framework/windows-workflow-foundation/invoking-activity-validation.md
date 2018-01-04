---
title: "叫用活動驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22fc7dc53f52b47be2da3313f678825d4362750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="a125e-102">叫用活動驗證</span><span class="sxs-lookup"><span data-stu-id="a125e-102">Invoking Activity Validation</span></span>
<span data-ttu-id="a125e-103">活動驗證提供的方法可在活動執行前識別及報告任何活動之組態中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a125e-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="a125e-104">在工作流程設計工具中修改工作流程時，若工作流程設計工具中顯示任何驗證錯誤或警告，就會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a125e-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="a125e-105">叫用工作流程時，也會在執行階段進行驗證，而且如果發生任何驗證錯誤，預設驗證邏輯會擲回 <xref:System.Activities.InvalidWorkflowException>。</span><span class="sxs-lookup"><span data-stu-id="a125e-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="a125e-106"> 提供 <xref:System.Activities.Validation.ActivityValidationServices> 類別，可讓工作流程應用程式和工具開發人員用來明確驗證活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-106"> provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="a125e-107">本主題描述如何使用 <xref:System.Activities.Validation.ActivityValidationServices> 執行活動驗證。</span><span class="sxs-lookup"><span data-stu-id="a125e-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="a125e-108">使用 ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="a125e-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="a125e-109"><xref:System.Activities.Validation.ActivityValidationServices> 具有兩個 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 負載，可用於叫用活動的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="a125e-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="a125e-110">第一個多載會採用要驗證的根活動，然後傳回驗證錯誤及警告的集合。</span><span class="sxs-lookup"><span data-stu-id="a125e-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="a125e-111">下列範例中會使用具有兩個必要引數的自訂 `Add` 活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="a125e-112">`Add` 活動用於 <xref:System.Activities.Statements.Sequence> 內部，但其兩個必要的引數並未繫結，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a125e-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a125e-113">您可以呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 來驗證此工作流程。</span><span class="sxs-lookup"><span data-stu-id="a125e-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="a125e-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 會傳回活動和任何子活動中包含的任何驗證錯誤或警告集合，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a125e-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a125e-115">在此工作流程範例中呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 時，會傳回兩個驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a125e-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="a125e-116">**錯誤： 未提供必要的活動引數 'Operand2' 的值。**</span><span class="sxs-lookup"><span data-stu-id="a125e-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="a125e-117">**錯誤： 未提供必要的活動引數 'Operand1' 的值。**</span><span class="sxs-lookup"><span data-stu-id="a125e-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="a125e-118">如果叫用這個工作流程，就會擲回 <xref:System.Activities.InvalidWorkflowException>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a125e-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a125e-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="a125e-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="a125e-120">**處理工作流程樹狀結構時發生下列錯誤：** </span><span class="sxs-lookup"><span data-stu-id="a125e-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="a125e-121">**'Add': 未提供必要的活動引數 'Operand2' 的值。** </span><span class="sxs-lookup"><span data-stu-id="a125e-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="a125e-122">**'Add': 未提供必要的活動引數 'Operand1' 的值。**</span><span class="sxs-lookup"><span data-stu-id="a125e-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="a125e-123">若要讓這個工作流程範例生效，就必須繫結 `Add` 活動的兩個必要引數。</span><span class="sxs-lookup"><span data-stu-id="a125e-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="a125e-124">在下列範例中，兩個必要引數會與結果值一同繫結於工作流程變數。</span><span class="sxs-lookup"><span data-stu-id="a125e-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="a125e-125">在此範例中，<xref:System.Activities.Activity%601.Result%2A> 引數會與兩個必要的引數一同繫結。</span><span class="sxs-lookup"><span data-stu-id="a125e-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="a125e-126"><xref:System.Activities.Activity%601.Result%2A> 引數不需繫結，若不繫結此引數，也不會導致驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a125e-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="a125e-127">如果工作流程中的其他位置會使用 <xref:System.Activities.Activity%601.Result%2A> 的值，工作流程作者必須負責繫結該值。</span><span class="sxs-lookup"><span data-stu-id="a125e-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="a125e-128">在根活動驗證必要的引數</span><span class="sxs-lookup"><span data-stu-id="a125e-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="a125e-129">如果工作流程的根活動含有引數，則在叫用該工作流程並將參數傳遞到該工作流程之前，這些都不會被繫結。</span><span class="sxs-lookup"><span data-stu-id="a125e-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="a125e-130">下列工作流程會通過驗證，但若叫用工作流程而未傳入必要的引數，則會擲回例外狀況，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a125e-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a125e-131">**System.ArgumentException： 根活動之引數設定不正確。**</span><span class="sxs-lookup"><span data-stu-id="a125e-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="a125e-132">**請修正工作流程定義，或提供輸入的值來修正這些錯誤：** </span><span class="sxs-lookup"><span data-stu-id="a125e-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="a125e-133">**'Add': 未提供必要的活動引數 'Operand2' 的值。** </span><span class="sxs-lookup"><span data-stu-id="a125e-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="a125e-134">**'Add': 未提供必要的活動引數 'Operand1' 的值。**</span><span class="sxs-lookup"><span data-stu-id="a125e-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="a125e-135">傳遞正確的引數後，工作流程就會成功完成，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a125e-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="a125e-136">在此範例中，根活動會宣告為 `Add`，而非上一個範例中的 `Activity`。</span><span class="sxs-lookup"><span data-stu-id="a125e-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="a125e-137">這樣可讓 `WorkflowInvoker.Invoke` 方法傳回單一整數，代表 `Add` 活動的結果 (而非 `out` 引數的字典)。</span><span class="sxs-lookup"><span data-stu-id="a125e-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="a125e-138">變數 `wf` 也可能已宣告為 `Activity<int>`。</span><span class="sxs-lookup"><span data-stu-id="a125e-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="a125e-139">驗證根引數時，主機應用程式必須負責確保叫用工作流程時，會傳遞所有必要的引數。</span><span class="sxs-lookup"><span data-stu-id="a125e-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="a125e-140">叫用命令式的程式碼式驗證</span><span class="sxs-lookup"><span data-stu-id="a125e-140">Invoking Imperative Code-Based Validation</span></span>  
 <span data-ttu-id="a125e-141">命令式的程式碼驗證提供一個簡單的方式，可讓活動提供與其本身相關的驗證，而且適用於衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="a125e-142">活動中會加入用來判斷任何驗證錯誤或警告的驗證程式碼。</span><span class="sxs-lookup"><span data-stu-id="a125e-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="a125e-143">在活動叫用驗證時，這些警告或錯誤包含在呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 所傳回的集合中。</span><span class="sxs-lookup"><span data-stu-id="a125e-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="a125e-144">在下列範例中，取自[基本驗證](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md)範例中，`CreateProduct`活動定義。</span><span class="sxs-lookup"><span data-stu-id="a125e-144">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="a125e-145">如果 `Cost` 大於 `Price`，就會將驗證錯誤加入至<xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a125e-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="a125e-146">在此範例中，會使用 `CreateProduct` 活動來設定工作流程。</span><span class="sxs-lookup"><span data-stu-id="a125e-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="a125e-147">在此工作流程中，`Cost` 大於 `Price`，而且未設定必要的 `Description` 引數。</span><span class="sxs-lookup"><span data-stu-id="a125e-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="a125e-148">叫用驗證時，會傳回下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="a125e-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="a125e-149">**錯誤： 成本必須小於或等於價格。**</span><span class="sxs-lookup"><span data-stu-id="a125e-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="a125e-150">**錯誤： 未提供必要的活動引數 'Description' 的值。**</span><span class="sxs-lookup"><span data-stu-id="a125e-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="a125e-151">自訂活動作者可以在活動的 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中提供驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="a125e-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="a125e-152">從 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 擲回的任何例外狀況都不會被視為驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a125e-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="a125e-153">這些例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中逸出，而且必須由呼叫端處理。</span><span class="sxs-lookup"><span data-stu-id="a125e-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="a125e-154">使用 ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="a125e-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="a125e-155">根據預設，當 <xref:System.Activities.Validation.ActivityValidationServices> 叫用驗證時，會評估活動樹狀結構中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="a125e-156"><xref:System.Activities.Validation.ValidationSettings> 允許透過設定驗證的三個屬性，以數種不同的方式自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="a125e-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="a125e-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 指定驗證程式是否應逐一查核整個活動樹狀結構，或者只需將驗證邏輯套用於所提供的活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="a125e-158">此值的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a125e-158">The default for this value is `false`.</span></span> <span data-ttu-id="a125e-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 會指定從型別至條件約束清單的其他條件約束對應。</span><span class="sxs-lookup"><span data-stu-id="a125e-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="a125e-160">為取得要驗證之活動樹狀結構中每個活動的基底型別，會查詢 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>。</span><span class="sxs-lookup"><span data-stu-id="a125e-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="a125e-161">如果找到相符的條件約束清單，會為該活動評估清單中的所有條件約束。</span><span class="sxs-lookup"><span data-stu-id="a125e-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="a125e-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 指定驗證程式是否應評估所有條件約束，或者只需評估 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 中指定的條件約束。</span><span class="sxs-lookup"><span data-stu-id="a125e-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="a125e-163">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="a125e-163">The default value is `false`.</span></span> <span data-ttu-id="a125e-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>和 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 適合讓工作流程主機作者用來新增額外的工作流程驗證，例如 FxCop 等工具的原則條件約束。</span><span class="sxs-lookup"><span data-stu-id="a125e-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="a125e-165">條件約束，請參閱[宣告式條件約束](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="a125e-165"> constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="a125e-166">若要使用 <xref:System.Activities.Validation.ValidationSettings>，請設定所需的屬性，然後在對 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中傳遞它。</span><span class="sxs-lookup"><span data-stu-id="a125e-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="a125e-167">在此範例中，會驗證包含 <xref:System.Activities.Statements.Sequence> 的活動 (該活動具有 `Add` 活動)。</span><span class="sxs-lookup"><span data-stu-id="a125e-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="a125e-168">`Add` 活動具有兩個必要引數。</span><span class="sxs-lookup"><span data-stu-id="a125e-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="a125e-169">`Add` 中會使用下列 <xref:System.Activities.Statements.Sequence> 活動，但不會繫結其兩個必要的引數。</span><span class="sxs-lookup"><span data-stu-id="a125e-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="a125e-170">針對下列範例，驗證執行時，<xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 會設定為 `true`，因此只會驗證根 <xref:System.Activities.Statements.Sequence> 活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="a125e-171">這個程式碼會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a125e-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="a125e-172">**沒有警告或錯誤**即使`Add`活動具有必要引數未繫結中，驗證會成功，因為會評估根活動。</span><span class="sxs-lookup"><span data-stu-id="a125e-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="a125e-173">若只驗證活動樹狀中的特定項目，例如要在設計工具中驗證單一活動的屬性變更，這種類型的驗證相當有用。</span><span class="sxs-lookup"><span data-stu-id="a125e-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="a125e-174">請注意，若叫用此工作流程，會評估工作流程中設定的完整驗證，而且可能會擲回 <xref:System.Activities.InvalidWorkflowException>。</span><span class="sxs-lookup"><span data-stu-id="a125e-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="a125e-175"><xref:System.Activities.Validation.ActivityValidationServices> 和 <xref:System.Activities.Validation.ValidationSettings> 只會設定主機明確叫用的驗證，不會設定叫用工作流程時所發生的驗證。</span><span class="sxs-lookup"><span data-stu-id="a125e-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
