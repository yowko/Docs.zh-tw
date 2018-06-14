---
title: DynamicActivity 建立
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 93435be69f90ca0b74dae6b934cb145fabb7afff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518098"
---
# <a name="dynamicactivity-creation"></a>DynamicActivity 建立
這個範例會示範在執行階段使用 <xref:System.Activities.DynamicActivity> 活動建立活動的兩種不同方式。  
  
 在這個範例中，將會在執行階段建立活動，活動的主體包含了含有 <xref:System.Activities.Statements.Sequence> 和 <xref:System.Activities.Statements.ForEach%601> 活動的 <xref:System.Activities.Statements.Assign%601> 活動。 整數輸入清單會傳遞到活動中並設定為屬性。 然後 <xref:System.Activities.Statements.ForEach%601> 活動會逐一查看值的清單並加以累積。 在 <xref:System.Activities.Statements.Assign%601> 活動中，平均值的計算方式是將累積值除以清單中的項目數，然後將它指派給平均值。  
  
 此範例會示範 <xref:System.Activities.DynamicActivity> 活動的使用，此活動會當做輸入引數流入變數中，並傳回值當做輸出引數。 此活動擁有名為 `Numbers` 的一個輸入引數，這個引數是整數的清單。 <xref:System.Activities.Statements.ForEach%601> 活動會逐一查看值的清單並加以累積。 在 <xref:System.Activities.Statements.Assign%601> 活動中，平均值的計算方式是將累積值除以清單中的項目數，然後將它指派給平均值。 平均值會當做名為 `Average` 的輸出引數傳回。  
  
 以程式設計方式建立動態活動時，將會宣告輸入和輸出，如下列程式碼範例所示。  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 下列程式碼範例會示範 `DynamicActivity` 的完整定義，它會計算清單中之值的平均值。  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 在 XAML 中建立時，將會宣告輸入和輸出，如下列範例所示。  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 XAML 可以透過 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 來以視覺方式建立。 如果它包含在 Visual Studio 專案中，請務必設定其 [建置動作] 為 [無] 以防止它正在進行編譯。 然後可以使用下列呼叫來動態載入 XAML。  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 可以使用透過程式設計方式或是載入 XAML 工作流程所建立的 <xref:System.Activities.DynamicActivity> 執行個體，如下列程式碼範例所示。 請注意，「 處理 」 傳遞給`WorkflowInvoker.Invoke`是"act"<xref:System.Activities.Activity>第一個程式碼範例中所定義。  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DynamicActivityCreation.sln 方案檔。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
## <a name="command-line-arguments"></a>命令列的引數  
 這個範例可接受命令列引數。 使用者可以為活動提供一份數字清單，以計算其平均值。 要使用的數字清單會當做以空格分隔的數字清單來傳遞。 例如，若要計算 5、10 和 32 的平均值，請使用下列命令列來叫用範例。  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`