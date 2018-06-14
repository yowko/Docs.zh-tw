---
title: 命令式的程式碼式驗證
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 87585050d7ab8c9adc5f0ac4ac5396862975cc25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515454"
---
# <a name="imperative-code-based-validation"></a>命令式的程式碼式驗證
命令式的程式碼驗證提供一個簡單的方式，可讓活動提供與其本身相關的驗證，而且適用於衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動。 活動中會加入用來判斷任何驗證錯誤或警告的驗證程式碼。  
  
## <a name="using-code-based-validation"></a>使用程式碼驗證  
 由衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動可支援程式碼驗證。 驗證碼可以放在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中，而且可以將驗證錯誤或警告加入至中繼資料引數。 在下列範例中，取自[基本驗證](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md)範例，如果`Cost`大於`Price`，將驗證錯誤加入至中繼資料。  
  
> [!NOTE]
>  請注意，`Cost`和 `Price` 不是活動的引數，而是在設計階段設定的屬性。 這就是為什麼可以在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中驗證其值的原因。 在設計階段不能驗證流經引數的資料值，因為在執行階段之前，資料不會流過，但是可以驗證活動引數，以確保已使用 `RequiredArgument` 屬性和多載群組來繫結這些引數。 此程式碼範例會查看 `RequiredArgument` 引數的 `Description` 屬性，如果未繫結，則會產生驗證錯誤。 必要的引數會涵蓋[所需的引數與多載群組](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)。  
  
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
  
 根據預設，當呼叫 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 時，會將驗證錯誤加入至中繼資料。 若要加入驗證警告，請使用採取 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 的 <xref:System.Activities.Validation.ValidationError> 多載，並設定 <xref:System.Activities.Validation.ValidationError> 屬性來指定 <xref:System.Activities.Validation.ValidationError.IsWarning%2A> 表示警告。  
  
 在工作流程設計工具中修改工作流程時，若工作流程設計工具中顯示任何驗證錯誤或警告，就會進行驗證。 叫用工作流程時，也會在執行階段進行驗證，而且如果發生任何驗證錯誤，預設驗證邏輯會擲回 <xref:System.Activities.InvalidWorkflowException>。 如需叫用驗證及存取的任何驗證警告或錯誤的詳細資訊，請參閱[叫用活動驗證](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)。  
  
 從 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 擲回的任何例外狀況都不會被視為驗證錯誤。 這些例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中逸出，而且必須由呼叫端處理。  
  
 程式碼驗證對於驗證包含程式碼的活動很有用，但工作流程中的其他活動並不會顯示出來。 宣告式條件約束驗證可讓您驗證活動及工作流程中的其他活動之間的關聯性，並涵蓋[宣告式條件約束](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)主題。
