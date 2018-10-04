---
title: 宣告式條件約束
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 5599513405c77aa213b329b085075660baed5c47
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580484"
---
# <a name="declarative-constraints"></a><span data-ttu-id="b44d3-102">宣告式條件約束</span><span class="sxs-lookup"><span data-stu-id="b44d3-102">Declarative Constraints</span></span>
<span data-ttu-id="b44d3-103">宣告式條件約束提供強大的驗證方法，適用於驗證活動及該活動與其他活動之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b44d3-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="b44d3-104">條件約束是在撰寫處理序期間針對活動所設定的，但工作流程主機亦可指定其他條件約束。</span><span class="sxs-lookup"><span data-stu-id="b44d3-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="b44d3-105">本主題介紹使用宣告式條件約束來提供活動驗證的概觀。</span><span class="sxs-lookup"><span data-stu-id="b44d3-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="b44d3-106">使用宣告式條件約束</span><span class="sxs-lookup"><span data-stu-id="b44d3-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="b44d3-107">條件約束是包含驗證邏輯的活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="b44d3-108">此條件約束活動可以用程式碼或 XAML 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="b44d3-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="b44d3-109">建立條件約束活動後，活動作者會將該條件約束加入至要驗證之活動的 <xref:System.Activities.Activity.Constraints%2A> 屬性，或者使用該條件約束來提供額外驗證 (使用 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 執行個體的 <xref:System.Activities.Validation.ValidationSettings> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="b44d3-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="b44d3-110">驗證邏輯可包含簡單驗證 (例如驗證活動的中繼資料)，但亦可執行將目前活動與其父系、子系及同層級活動之關聯性列入考量的驗證。</span><span class="sxs-lookup"><span data-stu-id="b44d3-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="b44d3-111">條件約束是使用 <xref:System.Activities.Validation.Constraint%601> 活動所撰寫的，同時會提供數個額外的驗證活動來輔助建立驗證錯誤及警告，以及提供有關工作流程中相關活動的資訊。</span><span class="sxs-lookup"><span data-stu-id="b44d3-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="b44d3-112">AssertValidation 與 AddValidationError</span><span class="sxs-lookup"><span data-stu-id="b44d3-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="b44d3-113"><xref:System.Activities.Validation.AssertValidation> 活動會驗證其 <xref:System.Activities.Validation.AssertValidation.Assertion%2A> 屬性所參考的運算式，如果運算式評估為 `false`，就會在 <xref:System.Activities.Validation.ValidationResults> 加入驗證錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="b44d3-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="b44d3-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> 屬性會描述驗證錯誤，而 <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> 屬性則會指出驗證失敗為錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="b44d3-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="b44d3-115"><xref:System.Activities.Validation.AssertValidation.IsWarning%2A> 的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b44d3-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="b44d3-116">下列範例會宣告條件約束，如果要驗證之活動的 <xref:System.Activities.Activity.DisplayName%2A> 長度為兩個字元以下，則會傳回驗證警告。</span><span class="sxs-lookup"><span data-stu-id="b44d3-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="b44d3-117"><xref:System.Activities.Validation.Constraint%601> 所用的泛型型別參數會指定該條件約束所驗證的活動型別。</span><span class="sxs-lookup"><span data-stu-id="b44d3-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="b44d3-118">這個條件約束會使用 <xref:System.Activities.Activity> 做為泛型型別，同時可用於驗證活動的所有型別。</span><span class="sxs-lookup"><span data-stu-id="b44d3-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 <span data-ttu-id="b44d3-119">若要指定活動的這個條件約束，需將其加入至活動的 <xref:System.Activities.Activity.Constraints%2A> 中，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b44d3-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 <span data-ttu-id="b44d3-120">主機也可以使用 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>，在工作流程中為活動指定這個條件約束，此部分將在下一節中說明。</span><span class="sxs-lookup"><span data-stu-id="b44d3-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="b44d3-121"><xref:System.Activities.Validation.AddValidationError> 活動會用於在不需評估運算式的情況下產生驗證錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="b44d3-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="b44d3-122">此活動的屬性與 <xref:System.Activities.Validation.AssertValidation> 相似，且可用於結合條件約束 (例如 <xref:System.Activities.Statements.If> 活動) 的流程控制活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="b44d3-123">工作流程關聯性活動</span><span class="sxs-lookup"><span data-stu-id="b44d3-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="b44d3-124">有幾種驗證活動可供使用，其提供有關正在驗證的活動在工作流程中的其他活動資訊。</span><span class="sxs-lookup"><span data-stu-id="b44d3-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="b44d3-125"><xref:System.Activities.Validation.GetParentChain> 會傳回活動集合，其中包含目前活動與根活動之間的所有活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="b44d3-126"><xref:System.Activities.Validation.GetChildSubtree> 會提供活動集合，其中包含遞迴模式中的子活動，且 <xref:System.Activities.Validation.GetWorkflowTree> 會取得工作流程中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="b44d3-127">在下列範例中，會定義 `CreateState` 活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="b44d3-128">`CreateState` 活動必須包含在 `CreateCountry` 活動中，而 `GetParent` 方法會傳回強制此要求的條件約束。</span><span class="sxs-lookup"><span data-stu-id="b44d3-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="b44d3-129">`GetParent` 會將 <xref:System.Activities.Validation.GetParentChain> 活動與 <xref:System.Activities.Statements.ForEach%601> 活動搭配使用，以檢查 `CreateState` 活動的父活動，判斷是否滿足要求。</span><span class="sxs-lookup"><span data-stu-id="b44d3-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();              
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }    
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();                          
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {                                     
            Body = new ActivityAction<CreateState,ValidationContext>  
            {                      
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result   
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {                                  
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context                                      
                            },  
                            Body = new ActivityAction<Activity>  
                            {     
                                Argument = parent,   
                                Handler = new If()  
                                {                                            
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),                                          
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }                                  
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),                                                                  
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a><span data-ttu-id="b44d3-130">其他條件約束</span><span class="sxs-lookup"><span data-stu-id="b44d3-130">Additional Constraints</span></span>  
 <span data-ttu-id="b44d3-131">工作流程主機作者可以為工作流程中的活動指定其他驗證條件約束，方法是建立條件約束並將它們加入至 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 執行個體的 <xref:System.Activities.Validation.ValidationSettings> 字典中。</span><span class="sxs-lookup"><span data-stu-id="b44d3-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="b44d3-132"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 中的每個項目均包含條件約束所套用的活動型別，以及該活動型別之其他約束條件的清單。</span><span class="sxs-lookup"><span data-stu-id="b44d3-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="b44d3-133">叫用工作流程的驗證時，指定型別的每個活動 (包括衍生類別) 都會評估該條件約束。</span><span class="sxs-lookup"><span data-stu-id="b44d3-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="b44d3-134">在這個範例中，會將上一節的 `ActivityDisplayNameIsNotSetWarning` 條件約束套用至工作流程中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="b44d3-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},       
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="b44d3-135">如果 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 的 <xref:System.Activities.Validation.ValidationSettings> 屬性是 `true`，則當透過呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 來叫用驗證時，只會評估指定的其他條件約束。</span><span class="sxs-lookup"><span data-stu-id="b44d3-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="b44d3-136">這項功能非常適合用於檢查工作流程中的特定驗證組態。</span><span class="sxs-lookup"><span data-stu-id="b44d3-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="b44d3-137">但是請注意，叫用工作流程時會評估工作流程中設定的驗證邏輯，而且必須通過驗證，工作流程才能順利開始。</span><span class="sxs-lookup"><span data-stu-id="b44d3-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="b44d3-138">如需有關如何叫用驗證的詳細資訊，請參閱 <<c0> [ 叫用活動驗證](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="b44d3-138">For more information about invoking validation, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>
