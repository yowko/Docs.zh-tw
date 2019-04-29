---
title: 變數與引數
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 29ce5222435b68ed13cbc967e58e72a937625e8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669481"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="590a9-102">變數與引數</span><span class="sxs-lookup"><span data-stu-id="590a9-102">Variables and Arguments</span></span>
<span data-ttu-id="590a9-103">在 Windows Workflow Foundation (WF) 中，變數表示資料的儲存體，而引數表示資料流程傳入和傳出活動。</span><span class="sxs-lookup"><span data-stu-id="590a9-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="590a9-104">活動有一組引數，且它們會構成活動的簽章。</span><span class="sxs-lookup"><span data-stu-id="590a9-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="590a9-105">此外，活動也包含變數的清單，開發人員可在設計工作流程時加入或移除其中的變數。</span><span class="sxs-lookup"><span data-stu-id="590a9-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="590a9-106">引數會使用傳回值的運算式來繫結。</span><span class="sxs-lookup"><span data-stu-id="590a9-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="590a9-107">變數</span><span class="sxs-lookup"><span data-stu-id="590a9-107">Variables</span></span>  
 <span data-ttu-id="590a9-108">變數是資料的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="590a9-108">Variables are storage locations for data.</span></span> <span data-ttu-id="590a9-109">變數會宣告為工作流程定義的一部分，</span><span class="sxs-lookup"><span data-stu-id="590a9-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="590a9-110">並負責執行階段的值，而這些值會儲存成工作流程執行個體狀態的一部分。</span><span class="sxs-lookup"><span data-stu-id="590a9-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="590a9-111">變數定義會指定變數的型別，以及選擇性地指定名稱。</span><span class="sxs-lookup"><span data-stu-id="590a9-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="590a9-112">下列程式碼顯示如何使用 <xref:System.Activities.Statements.Assign%601> 活動來宣告變數、將值指派至變數，然後使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台上顯示其值。</span><span class="sxs-lookup"><span data-stu-id="590a9-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="590a9-113">預設的值運算式可選擇性地指定為變數宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="590a9-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="590a9-114">變數亦可含有修飾詞。</span><span class="sxs-lookup"><span data-stu-id="590a9-114">Variables also can have modifiers.</span></span> <span data-ttu-id="590a9-115">例如，如果變數是唯讀，即可套用 <xref:System.Activities.VariableModifiers> 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="590a9-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="590a9-116">在下列範例中，會建立具有指派預設值的唯讀變數。</span><span class="sxs-lookup"><span data-stu-id="590a9-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="590a9-117">變數範圍</span><span class="sxs-lookup"><span data-stu-id="590a9-117">Variable Scoping</span></span>  
 <span data-ttu-id="590a9-118">執行階段時的變數存留期會等於宣告此變數的活動存留期。</span><span class="sxs-lookup"><span data-stu-id="590a9-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="590a9-119">當活動完成時會清除其變數，而且也不可再進行參照。</span><span class="sxs-lookup"><span data-stu-id="590a9-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="590a9-120">引數</span><span class="sxs-lookup"><span data-stu-id="590a9-120">Arguments</span></span>  
 <span data-ttu-id="590a9-121">活動作者會使用引數來定義資料流入與流出活動的方式。</span><span class="sxs-lookup"><span data-stu-id="590a9-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="590a9-122">每個引數都有指定的方向：<xref:System.Activities.ArgumentDirection.In>、<xref:System.Activities.ArgumentDirection.Out> 或 <xref:System.Activities.ArgumentDirection.InOut>。</span><span class="sxs-lookup"><span data-stu-id="590a9-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="590a9-123">工作流程執行階段會對資料進出活動的時機提供以下保證：</span><span class="sxs-lookup"><span data-stu-id="590a9-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="590a9-124">當活動開始執行時，會計算其所有輸入與輸入/輸出引數的值。</span><span class="sxs-lookup"><span data-stu-id="590a9-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="590a9-125">例如，不論何時呼叫 <xref:System.Activities.Argument.Get%2A>，傳回的值優先為執行階段所計算的值，然後才是其 `Execute` 的引動值。</span><span class="sxs-lookup"><span data-stu-id="590a9-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="590a9-126">當呼叫 <xref:System.Activities.InOutArgument%601.Set%2A> 時，執行階段會立即設定值。</span><span class="sxs-lookup"><span data-stu-id="590a9-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="590a9-127">引數可以選擇是否要指定它們的 <xref:System.Activities.Argument.EvaluationOrder%2A>。</span><span class="sxs-lookup"><span data-stu-id="590a9-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="590a9-128"><xref:System.Activities.Argument.EvaluationOrder%2A> 是指定評估引數順序之以零為起始的值。</span><span class="sxs-lookup"><span data-stu-id="590a9-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="590a9-129">根據預設，引數的預設評估順序未指定，而且等於 <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> 值。</span><span class="sxs-lookup"><span data-stu-id="590a9-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="590a9-130">設定 <xref:System.Activities.Argument.EvaluationOrder%2A> 為大於或等於零的值，以指定這個引數的評估順序。</span><span class="sxs-lookup"><span data-stu-id="590a9-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="590a9-131">Windows Workflow Foundation 會評估引數的指定的評估順序，依遞增順序排列。</span><span class="sxs-lookup"><span data-stu-id="590a9-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="590a9-132">請注意，未指定評估順序的引數會在有指定評估順序的引數之前先進行評估。</span><span class="sxs-lookup"><span data-stu-id="590a9-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="590a9-133">活動作者可使用強型別的機制來公開其引數。</span><span class="sxs-lookup"><span data-stu-id="590a9-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="590a9-134">藉由宣告型別 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 與 <xref:System.Activities.InOutArgument%601> 的屬性，即可完成此動作。</span><span class="sxs-lookup"><span data-stu-id="590a9-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="590a9-135">這可讓活動作者建立資料進出活動的相關特定合約。</span><span class="sxs-lookup"><span data-stu-id="590a9-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="590a9-136">定義活動的引數</span><span class="sxs-lookup"><span data-stu-id="590a9-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="590a9-137">藉由指定型別 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 與 <xref:System.Activities.InOutArgument%601> 的屬性，即可在活動上定義引數。</span><span class="sxs-lookup"><span data-stu-id="590a9-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="590a9-138">下列程式碼顯示如何定義帶入字串以顯示使用者，並傳回包含使用者回應字串之 `Prompt` 活動的引數。</span><span class="sxs-lookup"><span data-stu-id="590a9-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="590a9-139">傳回單一值的活動可衍生自 <xref:System.Activities.Activity%601>、<xref:System.Activities.NativeActivity%601> 或 <xref:System.Activities.CodeActivity%601>。</span><span class="sxs-lookup"><span data-stu-id="590a9-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="590a9-140">這些活動具有充分定義的 <xref:System.Activities.OutArgument%601> 具名 <xref:System.Activities.Activity%601.Result%2A>，其中包含活動的傳回值。</span><span class="sxs-lookup"><span data-stu-id="590a9-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="590a9-141">在工作流程中使用變數與引數</span><span class="sxs-lookup"><span data-stu-id="590a9-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="590a9-142">下列範例示範如何在工作流程中使用變數與引數。</span><span class="sxs-lookup"><span data-stu-id="590a9-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="590a9-143">工作流程會依照順序宣告三種變數：`var1`、`var2` 與 `var3`。</span><span class="sxs-lookup"><span data-stu-id="590a9-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="590a9-144">工作流程中的第一個活動是指派變數 `Assign` 值到變數 `var1` 的 `var2` 活動。</span><span class="sxs-lookup"><span data-stu-id="590a9-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="590a9-145">這之後的 `WriteLine` 活動會列印 `var2` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="590a9-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="590a9-146">下一步是指派變數 `Assign` 到變數 `var2` 的其他 `var3` 活動。</span><span class="sxs-lookup"><span data-stu-id="590a9-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="590a9-147">最後一步是另一個 `WriteLine` 活動，這個活動會列印 `var3` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="590a9-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="590a9-148">第一個 `Assign` 活動會使用明確表示活動引數繫結的 `InArgument<string>` 和 `OutArgument<string>`。</span><span class="sxs-lookup"><span data-stu-id="590a9-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="590a9-149">`InArgument<string>` 適用於 <xref:System.Activities.Statements.Assign.Value%2A>，因為該值會透過其 <xref:System.Activities.Statements.Assign%601> 引數流入 <xref:System.Activities.Statements.Assign.Value%2A> 活動中，而 `OutArgument<string>` 適用於 <xref:System.Activities.Statements.Assign.To%2A>，因為該值會從 <xref:System.Activities.Statements.Assign.To%2A> 引數流出到變數中。</span><span class="sxs-lookup"><span data-stu-id="590a9-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="590a9-150">第二個 `Assign` 活動會完成同樣的工作，並使用更精簡但使用隱含轉型的對等語法。</span><span class="sxs-lookup"><span data-stu-id="590a9-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="590a9-151">`WriteLine` 活動也會使用精簡語法。</span><span class="sxs-lookup"><span data-stu-id="590a9-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="590a9-152">在程式碼式活動中使用變數與引數</span><span class="sxs-lookup"><span data-stu-id="590a9-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="590a9-153">先前的範例示範如何在工作流程中使用引數與宣告式活動。</span><span class="sxs-lookup"><span data-stu-id="590a9-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="590a9-154">在程式碼式活動中也會使用引數與變數。</span><span class="sxs-lookup"><span data-stu-id="590a9-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="590a9-155">概念上，其用法很類似。</span><span class="sxs-lookup"><span data-stu-id="590a9-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="590a9-156">變數表示活動內的資料存放區，而引數表示資料對活動的流入或流出，且是由工作流程作者繫結程序至工作流程中表示資料流出或流入位置的其他變數或引數。</span><span class="sxs-lookup"><span data-stu-id="590a9-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="590a9-157">若要取得或設定活動中的變數或引數值，必須使用表示活動目前執行環境的活動內容。</span><span class="sxs-lookup"><span data-stu-id="590a9-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="590a9-158">這會由工作流程執行階段傳遞至活動的 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="590a9-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="590a9-159">在此範例中，會定義含有兩個 `Add` 引數的自訂 <xref:System.Activities.ArgumentDirection.In> 活動。</span><span class="sxs-lookup"><span data-stu-id="590a9-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="590a9-160">若要存取引數值，則會使用 <xref:System.Activities.Argument.Get%2A> 方法，且要使用工作流程執行階段所傳遞的內容。</span><span class="sxs-lookup"><span data-stu-id="590a9-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="590a9-161">如需有關引數、 變數和運算式在程式碼中的使用的詳細資訊，請參閱[撰寫工作流程、 活動和運算式使用命令式程式碼](authoring-workflows-activities-and-expressions-using-imperative-code.md)和[所需的引數與多載群組](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="590a9-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
