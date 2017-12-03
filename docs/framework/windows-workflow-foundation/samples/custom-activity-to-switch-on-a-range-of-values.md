---
title: "自訂活動以切換到值的範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4dcaf023960aab1989493475fe4e5306623adf8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>自訂活動以切換到值的範圍
這個範例示範如何建立可擴充 <xref:System.Activities.Statements.Switch%601> 用法的自訂活動。 傳統 <xref:System.Activities.Statements.Switch%601> 陳述式允許根據單一值的切換。 但有些商務狀況中活動必須根據值範圍來切換。 例如，當切換依據的值介於 1 和 5 之間時，活動可能會執行某個動作，當值介於 6 和 10 之間時執行另一個動作，並針對所有其他值執行預設動作。 這個自訂活動正是實現該狀況。  
  
## <a name="the-switchrange-activity"></a>SwitchRange 活動  
 `SwitchRange` 活動會在其運算式的結果值是包含在其中一個 `Cases` 的範圍時排定子活動。  
  
 下列程式碼範例為根據值範圍來切換的自訂活動。  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|屬性|描述|  
|-|-|  
|運算式|這是要進行評估並與 Cases 清單中的範圍進行比較的運算式。 運算式的結果為 T 類型。|  
|Cases|每個案例包含範圍 (From 和 To) 以及活動 (Body)。 運算式會進行評估並與範圍進行比較。 如果運算式結果是在其中一個案例的範圍中，則會執行對應活動。|  
|預設|當沒有相符案例時執行的活動。 設為 `null` 時，不會執行任何動作。|  
  
## <a name="caserange-class"></a>CaseRange 類別  
 `CaseRange` 類別代表 `SwitchRange` 活動中的範圍。 每個 `CaseRange` 執行個體都包含範圍 (由 `From` 和 `To` 組成) 以及 `Body` 活動 (當 `SwitchRange` 中的運算式評估結果是在範圍中時排程的活動)。  
  
 下列程式碼範例是 `CaseRange` 類別的定義。  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  此範例中定義的 `SwitchRange` 和 `CaseRange` 類別都是可與實作 `IComparable` 的任何類型 (如 <xref:System.Activities.Statements.Switch%601> 類別) 搭配使用的泛型類別。  
  
## <a name="sample-usage"></a>範例用法  
 下列程式碼範例會示範如何使用 `SwitchRange` 活動。  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 SwitchRange.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`