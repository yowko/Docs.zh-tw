---
title: "命令式的程式碼式驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 命令式的程式碼式驗證
命令式的程式碼驗證提供讓活動自我驗證的簡易方式，且適用於衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>和 <xref:System.Activities.NativeActivity> 的活動。在活動中加入判斷是否有任何驗證錯誤或警告的驗證程式碼。  
  
## 使用程式碼驗證  
 衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動支援程式碼驗證。可將驗證碼放置於 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫，且可將驗證錯誤或警告加入至中繼資料引數。在下列範例取自 [基本驗證](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) 的範例中，如果 `Cost` 大於 `Price`，就會將驗證錯誤加入至中繼資料。  
  
> [!NOTE]
>  請注意，`Cost`和 `Price`不是活動參數，而是在設計階段設定的屬性。這就是可以在<xref:System.Activities.CodeActivity.CacheMetadata%2A>覆寫中驗證其值的原因。設計階段不能驗證流經引數的資料值，因為在執行階段之前，資料不會流過，但可以驗證活動參數來確保已使用 `RequiredArgument`屬性和多載群組繫結這些引數。此程式碼範例會查看 `Description` 引數的 `RequiredArgument` 屬性，如果未繫結則會產生驗證錯誤。[必要引數與多載群組](../../../docs/framework/windows-workflow-foundation//required-arguments-and-overload-groups.md) 說明必要的參數。  
  
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
  
 根據預設，當呼叫 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 時，會將驗證錯誤加入至中繼資料。若要加入驗證警告，請使用採取 <xref:System.Activities.Validation.ValidationError> 的 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 多載，並設定 <xref:System.Activities.Validation.ValidationError.IsWarning%2A> 屬性來指定 <xref:System.Activities.Validation.ValidationError> 表示警告。  
  
 在工作流程設計工具中修改工作流程時，若工作流程設計工具中顯示任何驗證錯誤或警告，就會進行驗證。驗證也發生在執行階段當中叫用工作流程時，如果發生任何驗證錯誤，預設驗證邏輯會擲回  <xref:System.Activities.InvalidWorkflowException>。[!INCLUDE[crabout](../../../includes/crabout-md.md)] 叫用驗證及存取任何驗證警告或錯誤，請參閱 [叫用活動驗證](../../../docs/framework/windows-workflow-foundation//invoking-activity-validation.md)。  
  
 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 擲回的任何例外狀況都不會被視為驗證錯誤。這些例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中逸出，而且必須由呼叫端處理。  
  
 程式碼驗證對於驗證包含程式碼的活動很有用，但工作流程中的其他活動並不會顯示出來。宣告式條件約束驗證會提供驗證活動與工作流程中其他活動之間關係的功能，而[宣告式條件約束](../../../docs/framework/windows-workflow-foundation//declarative-constraints.md)中有涵蓋這個主題。