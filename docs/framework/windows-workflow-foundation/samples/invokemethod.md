---
title: InvokeMethod
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f988f206fbd84b7b7d47fb3bd540420601ba30c9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="invokemethod"></a><span data-ttu-id="569e4-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="569e4-102">InvokeMethod</span></span>
<span data-ttu-id="569e4-103">這個範例示範以不同的方式使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用類別的方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="569e4-104">方法屬於類別，且代表包含的作業集。</span><span class="sxs-lookup"><span data-stu-id="569e4-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="569e4-105"><xref:System.Activities.Statements.InvokeMethod> 活動讓您能夠針對物件或型別呼叫方法、傳遞參數，以及取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="569e4-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="569e4-106">方法可以採同步或非同步的方式叫用。</span><span class="sxs-lookup"><span data-stu-id="569e4-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="569e4-107">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="569e4-107">Sample Details</span></span>  
 <span data-ttu-id="569e4-108">這個範例使用 <xref:System.Activities.Statements.InvokeMethod> 活動執行下列案例：</span><span class="sxs-lookup"><span data-stu-id="569e4-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="569e4-109">叫用不含參數的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="569e4-110">使用兩個參數 (<xref:System.String> 和 <xref:System.Int32>) 叫用執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="569e4-111">使用兩個參數 (<xref:System.String> 和 <xref:System.Int32>) 和 <xref:System.String>[] 型別的參數陣列叫用執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="569e4-112">使用型別 <xref:System.Int32> 的兩個參數和型別 <xref:System.Int32> 的結果叫用執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="569e4-113">在這個案例中，結果值會繫結至變數並且在另一個活動中使用。</span><span class="sxs-lookup"><span data-stu-id="569e4-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="569e4-114">該值會使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台中顯示。</span><span class="sxs-lookup"><span data-stu-id="569e4-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="569e4-115">使用 <xref:System.String> 和 <xref:System.Int32> 型別的兩個參數叫用靜態方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="569e4-116">使用型別 <xref:System.String> 的一個泛型參數叫用執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="569e4-117">使用 <xref:System.String> 和 <xref:System.Int32> 型別的兩個泛型參數叫用靜態方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="569e4-118">叫用執行個體方法，該方法的其中一個參數是由型別 <xref:System.String> 的參考所傳遞。</span><span class="sxs-lookup"><span data-stu-id="569e4-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="569e4-119">在這個案例中，參考參數會繫結至變數 (`outParam`) 並且在另一個活動中使用。</span><span class="sxs-lookup"><span data-stu-id="569e4-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="569e4-120">它會使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台上顯示。</span><span class="sxs-lookup"><span data-stu-id="569e4-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="569e4-121">叫用非同步執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="569e4-122">使用兩個 <xref:System.Activities.Statements.InvokeMethod> 活動在物件的同一個執行個體上叫用兩個不同的方法。</span><span class="sxs-lookup"><span data-stu-id="569e4-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="569e4-123">在物件的執行個體中儲存值。</span><span class="sxs-lookup"><span data-stu-id="569e4-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="569e4-124">從物件的執行個體擷取值。</span><span class="sxs-lookup"><span data-stu-id="569e4-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="569e4-125">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="569e4-125">To use this sample</span></span>  
 <span data-ttu-id="569e4-126">這個範例會以兩種版本提供。</span><span class="sxs-lookup"><span data-stu-id="569e4-126">This sample is provided in two versions.</span></span> <span data-ttu-id="569e4-127">此範例的第一個版本示範如何使用<xref:System.Activities.Statements.InvokeMethod>透過 C# 程式碼使用 Windows Workflow Foundation (WF) 的程式設計模型，並可以在 CodedWorkflow\CS 資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="569e4-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="569e4-128">這個範例的第二個版本示範使用 XAML 的 <xref:System.Activities.Statements.InvokeMethod> 使用方式，這個版本可以在 DesignerWorkflow\CS 資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="569e4-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="569e4-129">若要執行編碼的工作流程範例</span><span class="sxs-lookup"><span data-stu-id="569e4-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="569e4-130">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CodedWorkflow\CS 資料夾中的 [InvokeMethodUsage.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="569e4-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="569e4-131">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="569e4-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="569e4-132">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="569e4-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="569e4-133">若要執行設計工具工作流程範例</span><span class="sxs-lookup"><span data-stu-id="569e4-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="569e4-134">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DesignerWorkflow\CS 資料夾中的 [InvokeMethodUsage.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="569e4-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="569e4-135">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="569e4-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="569e4-136">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="569e4-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="569e4-137">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="569e4-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="569e4-138">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="569e4-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="569e4-139">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="569e4-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="569e4-140">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="569e4-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`