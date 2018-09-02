---
title: 非泛型 ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: b94ad54d248af7f6ad45c11b9860dd415db840f9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419313"
---
# <a name="non-generic-foreach"></a>非泛型 ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 工具箱中隨附的控制流程的活動，包括一組<xref:System.Activities.Statements.ForEach%601>，允許逐一<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`集合。  
  
 <xref:System.Activities.Statements.ForEach%601> 需要其<xref:System.Activities.Statements.ForEach%601.Values%2A>類型的屬性<!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`。 這會防止使用者逐一查看資料結構，可實作<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`介面 (例如<xref:System.Collections.ArrayList>)。 非泛型 <xref:System.Activities.Statements.ForEach%601> 版本沒有這項需求，但在執行階段更複雜，以確保集合中數值型別的相容性。  
  
 這個範例示範如何實作非泛型 <xref:System.Activities.Statements.ForEach%601> 活動及其設計工具。 這個活動可用來逐一查看 <xref:System.Collections.ArrayList>。  
  
## <a name="foreach-activity"></a>ForEach 活動  
 C#/VB `foreach` 陳述式會列舉集合項目，並針對集合的每個項目執行內嵌陳述式。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 的 `foreach` 對應活動為 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。 <xref:System.Activities.Statements.ForEach%601> 活動包含值清單和主體。 在執行階段，會列舉此清單，並針對清單中的每個值執行主體。  
  
 在大部分情況下，泛型活動版本應該是慣用方案，因為它涵蓋大部分使用狀況，也提供編譯階段的類型檢查。 非泛型版本可用來逐一查看實作非泛型 <xref:System.Collections.IEnumerable> 介面的型別。  
  
## <a name="class-definition"></a>類別定義  
 下列程式碼範例示範非泛型 `ForEach` 活動的定義。  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body (選擇性)  
 <xref:System.Activities.ActivityAction> 型別的 <xref:System.Object>，針對集合中的每個項目來執行。 每個個別項目透過 `Argument` 屬性傳遞至 Body。  
  
 Values (選擇性)  
 逐一查看的項目集合。 確認所有集合項目具有相容型別的作業是在執行階段進行。  
  
## <a name="example-of-using-foreach"></a>使用 ForEach 的範例  
 下列程式碼示範如何在應用程式中使用 ForEach 活動。  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|條件|訊息|嚴重性|例外狀況類型|  
|---------------|-------------|--------------|--------------------|  
|Values 為 `null`。|未提供必要活動引數 'Values' 的值。|錯誤|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach 設計工具  
 此範例的活動設計工具在外觀上與針對內建 <xref:System.Activities.Statements.ForEach%601> 活動所提供的設計工具類似。 在工具箱 中的設計工具隨即出現**範例**，**非泛型活動**類別目錄。 名為設計工具**ForEachWithBodyFactory**在工具箱中，因為活動會公開<xref:System.Activities.Presentation.IActivityTemplateFactory>在工具箱中，這會建立活動有適當設定<xref:System.Activities.ActivityAction>。  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>若要執行這個範例  
  
1.  將您選擇的專案設定為方案的啟始專案：  
  
    1.  **CodeTestClient**示範如何使用使用程式碼的活動。  
  
    2.  **DesignerTestClient**示範如何使用設計工具內的活動。  
  
2.  建置並執行專案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
