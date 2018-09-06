---
title: 非泛型 ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43772763"
---
# <a name="non-generic-parallelforeach"></a>非泛型 ParallelForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 工具箱中隨附的控制流程的活動，包括一組<xref:System.Activities.Statements.ParallelForEach%601>，允許逐一<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`集合。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> 需要其<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>類型的屬性<!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`。 這會防止使用者逐一查看資料結構，可實作<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`介面 (例如<xref:System.Collections.ArrayList>)。 非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 版本沒有這項需求，但在執行階段更複雜，以確保集合中數值型別的相容性。  
  
 這個範例示範如何實作非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動及其設計工具。 這個活動可用來逐一查看 <xref:System.Collections.ArrayList>。  
  
## <a name="parallelforeach-activity"></a>ParallelForEach 活動  
 C#/VB `foreach` 陳述式會列舉集合項目，並針對集合的每個項目執行內嵌陳述式。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 對應活動為 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。 <xref:System.Activities.Statements.ForEach%601> 活動包含值清單和主體。 在執行階段，會列舉此清單，並針對清單中的每個值執行主體。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> 具有 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，所以如果 <xref:System.Activities.Statements.ParallelForEach%601> 的評估傳回 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，`true` 活動就可以早一點完成。 在每次反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>。  
  
 在大部分情況下，泛型版本的活動應該是慣用方案，因為它涵蓋大部分使用狀況，也提供編譯階段的型別檢查。 非泛型版本可用來逐一查看實作非泛型 <xref:System.Collections.IEnumerable> 介面的型別。  
  
## <a name="class-definition"></a>類別定義  
 下列程式碼範例示範非泛型 `ParallelForEach` 活動的定義。  
  
```  
[ContentProperty("Body")]  
public class ParallelForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    public Activity<bool> CompletionCondition  
    [DefaultValue(null)]  
    [DependsOn("CompletionCondition")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body (選擇性)  
 <xref:System.Activities.ActivityAction> 型別的 <xref:System.Object>，針對集合中的每個項目來執行。 每個個別項目都會透過 Argument 屬性傳遞至 Body。  
  
 Values (選擇性)  
 逐一查看的項目集合。 確認所有集合項目具有相容型別的作業是在執行階段進行。  
  
 CompletionCondition (選擇性)  
 在任何反覆運算完成之後，都會評估 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性。 如果評估為 `true`，則會取消已排程的擱置中反覆運算。 如果並未設定此屬性，則分支集合中的所有活動會執行到完成為止。  
  
## <a name="example-of-using-parallelforeach"></a>使用 ParallelForEach 的範例  
 下列程式碼示範如何在應用程式中使用 ParallelForEach 活動。  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ParallelForEach  
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
  
## <a name="parallelforeach-designer"></a>ParallelForEach 設計工具  
 此範例的活動設計工具在外觀上與針對內建 <xref:System.Activities.Statements.ParallelForEach%601> 活動所提供的設計工具類似。 在工具箱 中的設計工具隨即出現**範例**，**非泛型活動**類別目錄。 名為設計工具**ParallelForEachWithBodyFactory**在工具箱中，因為活動會公開<xref:System.Activities.Presentation.IActivityTemplateFactory>建立有適當設定的 [活動工具箱] 中<xref:System.Activities.ActivityAction>。  
  
```  
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()  
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
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  將您選擇的專案設定為方案的啟始專案。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
