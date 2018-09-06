---
title: LINQ to Objects 活動
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891576"
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="0bad1-102">LINQ to Objects 活動</span><span class="sxs-lookup"><span data-stu-id="0bad1-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="0bad1-103">這個範例示範如何建立活動，以使用 LINQ to Objects 查詢集合項目。</span><span class="sxs-lookup"><span data-stu-id="0bad1-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="0bad1-104">FindInCollection 的活動詳細資料</span><span class="sxs-lookup"><span data-stu-id="0bad1-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="0bad1-105">這個活動可讓使用者使用 LINQ to Objects 查詢記憶體中的集合項目。</span><span class="sxs-lookup"><span data-stu-id="0bad1-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="0bad1-106">您必須提供 Lambda 運算式形式的 LINQ 述詞來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="0bad1-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="0bad1-107">這個活動可以與 <xref:System.Activities.Statements.AddToCollection%601> 活動搭配使用。</span><span class="sxs-lookup"><span data-stu-id="0bad1-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="0bad1-108">下表詳細說明活動的屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="0bad1-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="0bad1-109">屬性或傳回值</span><span class="sxs-lookup"><span data-stu-id="0bad1-109">Property or Return Value</span></span>|<span data-ttu-id="0bad1-110">描述</span><span class="sxs-lookup"><span data-stu-id="0bad1-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="0bad1-111">`Collection` 屬性</span><span class="sxs-lookup"><span data-stu-id="0bad1-111">`Collection` property</span></span>|<span data-ttu-id="0bad1-112">指定來源集合的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0bad1-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="0bad1-113">`Predicate` 屬性</span><span class="sxs-lookup"><span data-stu-id="0bad1-113">`Predicate` property</span></span>|<span data-ttu-id="0bad1-114">必要屬性，指定 Lambda 運算式形式的集合篩選。</span><span class="sxs-lookup"><span data-stu-id="0bad1-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="0bad1-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="0bad1-115">Return Value</span></span>|<span data-ttu-id="0bad1-116">篩選的集合。</span><span class="sxs-lookup"><span data-stu-id="0bad1-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="0bad1-117">使用自訂活動的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="0bad1-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="0bad1-118">下列程式碼範例使用 `FindInCollection` 自訂活動，在員工集合中尋找 `Role` 屬性設為 `Manager` 且 `Location` 屬性設為 `Redmond` 的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="0bad1-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="0bad1-119">下列程式碼示範如何建立工作流程程式，以使用自訂 FindInCollection 活動、<xref:System.Activities.Statements.AddToCollection%601> 和 <xref:System.Activities.Statements.ForEach%601> 活動，在集合中填入員工，尋找有開發人員角色且位於 Redmond 的所有員工，然後逐一查看結果清單。</span><span class="sxs-lookup"><span data-stu-id="0bad1-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0bad1-120">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="0bad1-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="0bad1-121">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 LinqToObjects.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="0bad1-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0bad1-122">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="0bad1-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0bad1-123">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="0bad1-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0bad1-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0bad1-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0bad1-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0bad1-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0bad1-126">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0bad1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0bad1-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0bad1-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="0bad1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bad1-128">See Also</span></span>  
 [<span data-ttu-id="0bad1-129">Lambda 運算式 （C# 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="0bad1-129">Lambda Expressions (C# Programming Guide)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="0bad1-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="0bad1-130">LINQ to Objects</span></span>](https://go.microsoft.com/fwlink/?LinkID=150380)
