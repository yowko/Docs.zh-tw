---
title: "宣告式條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 宣告式條件約束
宣告式條件約束提供強大的驗證方法，適用於驗證活動及該活動與其他活動之間的關聯性。條件約束是在撰寫處理序期間針對活動所設定的，但工作流程主機亦可指定其他條件約束。本主題介紹使用宣告式條件約束來提供活動驗證的概觀。  
  
## 使用宣告式條件約束  
 條件約束是包含驗證邏輯的活動。此條件約束活動可在程式碼或 XAML 中撰寫。一旦建立條件約束活動後，活動作者就會將該條件約束加入至要驗證之活動的 <xref:System.Activities.Activity.Constraints%2A> 屬性，或者使用該條件約束來提供額外驗證 \(使用 <xref:System.Activities.Validation.ValidationSettings> 執行個體的 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 屬性\)。驗證邏輯可包含簡單驗證 \(例如驗證活動的中繼資料\)，但亦可執行將目前活動與其父系、子系及同層級活動之關聯性列入考量的驗證。條件約束是使用 <xref:System.Activities.Validation.Constraint%601> 活動所撰寫的，同時會提供數個額外的驗證活動來輔助建立驗證錯誤及警告，以及提供有關工作流程中相關活動的資訊。  
  
### AssertValidation 與 AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> 活動會驗證其 <xref:System.Activities.Validation.AssertValidation.Assertion%2A> 屬性所參考的運算式，如果運算式評估為 `false`，就會在 <xref:System.Activities.Validation.ValidationResults> 加入驗證錯誤或警告。<xref:System.Activities.Validation.AssertValidation.Message%2A> 屬性會描述驗證錯誤，而 <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> 屬性則會指出驗證失敗為錯誤或警告。<xref:System.Activities.Validation.AssertValidation.IsWarning%2A> 的預設值為 `false`。  
  
 下列範例會宣告條件約束，如果要驗證之活動的 <xref:System.Activities.Activity.DisplayName%2A> 長度為兩個字元以下，則會傳回驗證警告。<xref:System.Activities.Validation.Constraint%601> 所用的泛型型別參數會指定該條件約束所驗證的活動型別。這個條件約束會使用 <xref:System.Activities.Activity> 做為泛型型別，同時可用於驗證活動的所有型別。  
  
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
  
 若要指定活動的這個條件約束，需將其加入至活動的 <xref:System.Activities.Activity.Constraints%2A> 中，如下列範例程式碼所示。  
  
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
  
 使用 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 的主機亦可為工作流程中的活動指定這個條件約束，此部分將在下一節中說明。  
  
 <xref:System.Activities.Validation.AddValidationError> 活動會用於在不需評估運算式的情況下產生驗證錯誤或警告。此活動的屬性與 <xref:System.Activities.Validation.AssertValidation> 相似，且可用於結合條件約束 \(例如 <xref:System.Activities.Statements.If> 活動\) 的流程控制活動。  
  
### 工作流程關聯性活動  
 可使用幾種驗證活動，提供有關正在驗證的活動在工作流程中的其他活動的資訊。<xref:System.Activities.Validation.GetParentChain> 回傳回包含目前活動和根活動之間所有活動的活動集合。<xref:System.Activities.Validation.GetChildSubtree> 提供活動集合，其中包含遞迴模式中的子活動，且  <xref:System.Activities.Validation.GetWorkflowTree> 會取得工作流程中的所有活動。  
  
 在下列取自 [活動關聯性驗證](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) 的範例中，會定義 `CreateState` 活動。`CreateState`活動必須包含在 `CreateCountry`活動中，而 `GetParent`方法則會傳回強制此要求的條件約束。`GetParent`使用 <xref:System.Activities.Validation.GetParentChain>活動結合  <xref:System.Activities.Statements.ForEach%601>活動檢查 `CreateState` 活動的父活動，以確定是否滿足要求。  
  
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
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] Windows Workflow Foundation 的[驗證](../../../docs/framework/windows-workflow-foundation/samples/validation.md)範例。  
  
## 其他條件約束  
 工作流程主機作者可以為工作流程中的活動指定其他驗證條件約束，方法是建立條件約束並將它們加入至 <xref:System.Activities.Validation.ValidationSettings> 執行個體的 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 字典中。<xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 中的每個項目均包含條件約束所套用的活動型別，以及該活動型別之其他約束條件的清單。叫用工作流程的驗證時，指定型別的每個活動 \(包括衍生類別\) 都會評估該條件約束。在這個範例中，會將上一節的 `ActivityDisplayNameIsNotSetWarning` 條件約束套用至工作流程中的所有活動。  
  
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
  
 如果 <xref:System.Activities.Validation.ValidationSettings> 的 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 屬性是 `true`，則當透過呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 來叫用驗證時，只會評估指定的其他條件約束。這項功能非常適合用於檢查工作流程中的特定驗證組態。但是請注意，叫用工作流程時會評估工作流程中設定的驗證邏輯，而且必須通過驗證，工作流程才能順利開始。[!INCLUDE[crabout](../../../includes/crabout-md.md)] 叫用驗證，請參閱 [叫用活動驗證](../../../docs/framework/windows-workflow-foundation//invoking-activity-validation.md)。