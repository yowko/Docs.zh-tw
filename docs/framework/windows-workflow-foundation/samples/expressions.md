---
title: Expressions2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c988f41966f6e7bbd87fc4552de15b28117ecde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="expressions"></a><span data-ttu-id="dc00f-102">運算式</span><span class="sxs-lookup"><span data-stu-id="dc00f-102">Expressions</span></span>
<span data-ttu-id="dc00f-103">這個範例示範如何在工作流程中使用基本運算式。</span><span class="sxs-lookup"><span data-stu-id="dc00f-103">This sample demonstrates how to use basic expressions in a workflow.</span></span> <span data-ttu-id="dc00f-104">其中包含的工作流程會計算某虛構公司兩個員工的基本薪資統計資料。</span><span class="sxs-lookup"><span data-stu-id="dc00f-104">It consists of a workflow that calculates basic salary statistics for two employees of a fictitious company.</span></span> <span data-ttu-id="dc00f-105">兩個類別 `Employee` 和 `SalaryStats` 定義於 Employee.cs 和 SalaryStats.cs。</span><span class="sxs-lookup"><span data-stu-id="dc00f-105">Two classes, `Employee` and `SalaryStats`, are defined in Employee.cs and SalaryStats.cs.</span></span> <span data-ttu-id="dc00f-106">工作流程中使用這些類別，示範如何對複雜類型的變數屬性執行簡單算術和字串運算。</span><span class="sxs-lookup"><span data-stu-id="dc00f-106">These classes are used in a workflow that shows how to perform simple arithmetic and string operations on properties of variables of complex types.</span></span>  
  
 <span data-ttu-id="dc00f-107">薪資計算工作流程同時以 XAML 和 C# 定義，示範兩種撰寫樣式。</span><span class="sxs-lookup"><span data-stu-id="dc00f-107">The salary calculation workflow is defined both in XAML and in C# to demonstrate the two authoring styles.</span></span> <span data-ttu-id="dc00f-108">XAML 版本是包含於 SalaryCalculation.xaml，可在工作流程設計工具中檢視和編輯。</span><span class="sxs-lookup"><span data-stu-id="dc00f-108">The XAML version is contained in SalaryCalculation.xaml and can be viewed and edited in the workflow designer.</span></span> <span data-ttu-id="dc00f-109">C# 版本是位於 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="dc00f-109">The C# version resides in Program.cs.</span></span> <span data-ttu-id="dc00f-110">XAML 中使用的運算式符合 Visual Basic 語法，會使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 運算式活動來執行。</span><span class="sxs-lookup"><span data-stu-id="dc00f-110">The expressions used in XAML conform to Visual Basic syntax, and use <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> expression activities to execute.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dc00f-111">請參閱 < Visual Basic 運算式， [Visual Basic 運算式](http://go.microsoft.com/fwlink/?LinkId=165912)。</span><span class="sxs-lookup"><span data-stu-id="dc00f-111"> Visual Basic expressions see, [Visual Basic Expressions](http://go.microsoft.com/fwlink/?LinkId=165912).</span></span> <span data-ttu-id="dc00f-112">另一方面，C# 運算式是撰寫為 Lambda 運算式，會使用 <xref:System.Activities.Expressions.LambdaValue%601> 和 <xref:System.Activities.Expressions.LambdaReference%601> 運算式活動。</span><span class="sxs-lookup"><span data-stu-id="dc00f-112">On the other hand, expressions in C# are written as lambda expressions and use <xref:System.Activities.Expressions.LambdaValue%601> and <xref:System.Activities.Expressions.LambdaReference%601> expression activities.</span></span> <span data-ttu-id="dc00f-113">將運算式撰寫為 Lambda 運算式允許 C# 編譯器提供語法反白顯示和靜態驗證。</span><span class="sxs-lookup"><span data-stu-id="dc00f-113">Writing expressions as lambda expressions allows the C# compiler to provide syntax highlighting and static verification.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dc00f-114">lambda 運算式，在 C# 中，請參閱[Lambda 運算式 （C# 程式設計手冊）](http://go.microsoft.com/fwlink/?LinkId=182082)。</span><span class="sxs-lookup"><span data-stu-id="dc00f-114"> lambda expressions in C#, see [Lambda Expressions (C# Programming Guide)](http://go.microsoft.com/fwlink/?LinkId=182082).</span></span> <span data-ttu-id="dc00f-115">如果在程式碼中使用 Visual Basic 來撰寫工作流程，則會使用 Visual Basic Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="dc00f-115">If a workflow is authored in code using Visual Basic, then Visual Basic lambda expressions are used.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dc00f-116">lambda 運算式，在 Visual Basic，請參閱[Lambda 運算式 (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437)。</span><span class="sxs-lookup"><span data-stu-id="dc00f-116"> lambda expressions in Visual Basic, see [Lambda Expressions (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dc00f-117">關於編寫工作流程使用程式碼，請參閱[撰寫工作流程、 活動和運算式使用命令式程式碼](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="dc00f-117"> about authoring workflows using code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="dc00f-118">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="dc00f-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="dc00f-119">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 Expressions.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="dc00f-119">Open the Expressions.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="dc00f-120">按下 CTRL + SHIFT + B 以建置方案，或選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="dc00f-120">Press CTRL+SHIFT+B to build the solution or select **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc00f-121">若要在 Visual Studio 設計工具中開啟 SalaryCalculation.xaml，您必須先編譯專案，確認 `Employee` 和 `SalaryStats` 類別可用於設計工具。</span><span class="sxs-lookup"><span data-stu-id="dc00f-121">To open SalaryCalculation.xaml in the Visual Studio designer, you must first compile your project to ensure that `Employee` and `SalaryStats` classes are available to the designer.</span></span>  
  
3.  <span data-ttu-id="dc00f-122">成功建置後，按 F5 或選取**開始偵錯**從**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="dc00f-122">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="dc00f-123">或者您可以按 Ctrl + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。</span><span class="sxs-lookup"><span data-stu-id="dc00f-123">Alternatively you can press Ctrl+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc00f-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="dc00f-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dc00f-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="dc00f-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dc00f-126">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="dc00f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc00f-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="dc00f-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`  
  
## <a name="see-also"></a><span data-ttu-id="dc00f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc00f-128">See Also</span></span>
