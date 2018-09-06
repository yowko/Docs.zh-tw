---
title: DynamicActivity 建立
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777483"
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="512d5-102">DynamicActivity 建立</span><span class="sxs-lookup"><span data-stu-id="512d5-102">DynamicActivity Creation</span></span>
<span data-ttu-id="512d5-103">這個範例會示範在執行階段使用 <xref:System.Activities.DynamicActivity> 活動建立活動的兩種不同方式。</span><span class="sxs-lookup"><span data-stu-id="512d5-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="512d5-104">在這個範例中，將會在執行階段建立活動，活動的主體包含了含有 <xref:System.Activities.Statements.Sequence> 和 <xref:System.Activities.Statements.ForEach%601> 活動的 <xref:System.Activities.Statements.Assign%601> 活動。</span><span class="sxs-lookup"><span data-stu-id="512d5-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="512d5-105">整數輸入清單會傳遞到活動中並設定為屬性。</span><span class="sxs-lookup"><span data-stu-id="512d5-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="512d5-106">然後 <xref:System.Activities.Statements.ForEach%601> 活動會逐一查看值的清單並加以累積。</span><span class="sxs-lookup"><span data-stu-id="512d5-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="512d5-107">在 <xref:System.Activities.Statements.Assign%601> 活動中，平均值的計算方式是將累積值除以清單中的項目數，然後將它指派給平均值。</span><span class="sxs-lookup"><span data-stu-id="512d5-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="512d5-108">此範例會示範 <xref:System.Activities.DynamicActivity> 活動的使用，此活動會當做輸入引數流入變數中，並傳回值當做輸出引數。</span><span class="sxs-lookup"><span data-stu-id="512d5-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="512d5-109">此活動擁有名為 `Numbers` 的一個輸入引數，這個引數是整數的清單。</span><span class="sxs-lookup"><span data-stu-id="512d5-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="512d5-110"><xref:System.Activities.Statements.ForEach%601> 活動會逐一查看值的清單並加以累積。</span><span class="sxs-lookup"><span data-stu-id="512d5-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="512d5-111">在 <xref:System.Activities.Statements.Assign%601> 活動中，平均值的計算方式是將累積值除以清單中的項目數，然後將它指派給平均值。</span><span class="sxs-lookup"><span data-stu-id="512d5-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="512d5-112">平均值會當做名為 `Average` 的輸出引數傳回。</span><span class="sxs-lookup"><span data-stu-id="512d5-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="512d5-113">以程式設計方式建立動態活動時，將會宣告輸入和輸出，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="512d5-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="512d5-114">下列程式碼範例會示範 `DynamicActivity` 的完整定義，它會計算清單中之值的平均值。</span><span class="sxs-lookup"><span data-stu-id="512d5-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
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
  
 <span data-ttu-id="512d5-115">在 XAML 中建立時，將會宣告輸入和輸出，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="512d5-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="512d5-116">XAML 可以透過 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 來以視覺方式建立。</span><span class="sxs-lookup"><span data-stu-id="512d5-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="512d5-117">如果它包含在 Visual Studio 專案，請務必設定其 [建置動作] 為 「 無 」 以防止它正在進行編譯。</span><span class="sxs-lookup"><span data-stu-id="512d5-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="512d5-118">然後可以使用下列呼叫來動態載入 XAML。</span><span class="sxs-lookup"><span data-stu-id="512d5-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="512d5-119">可以使用透過程式設計方式或是載入 XAML 工作流程所建立的 <xref:System.Activities.DynamicActivity> 執行個體，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="512d5-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="512d5-120">請注意，「 處理 」 傳遞至`WorkflowInvoker.Invoke`是 「 動作 」<xref:System.Activities.Activity>第一個程式碼範例中所定義。</span><span class="sxs-lookup"><span data-stu-id="512d5-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="512d5-121">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="512d5-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="512d5-122">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DynamicActivityCreation.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="512d5-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="512d5-123">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="512d5-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="512d5-124">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="512d5-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="512d5-125">命令列的引數</span><span class="sxs-lookup"><span data-stu-id="512d5-125">Command line arguments</span></span>  
 <span data-ttu-id="512d5-126">這個範例可接受命令列引數。</span><span class="sxs-lookup"><span data-stu-id="512d5-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="512d5-127">使用者可以為活動提供一份數字清單，以計算其平均值。</span><span class="sxs-lookup"><span data-stu-id="512d5-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="512d5-128">要使用的數字清單會當做以空格分隔的數字清單來傳遞。</span><span class="sxs-lookup"><span data-stu-id="512d5-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="512d5-129">例如，若要計算 5、10 和 32 的平均值，請使用下列命令列來叫用範例。</span><span class="sxs-lookup"><span data-stu-id="512d5-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="512d5-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="512d5-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="512d5-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="512d5-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="512d5-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="512d5-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="512d5-133">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="512d5-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="512d5-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="512d5-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`