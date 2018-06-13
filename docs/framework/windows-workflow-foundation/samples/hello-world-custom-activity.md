---
title: Hello World 自訂活動
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: 35ae5933515b3280b0d8d95157c8dd5f40f7b320
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515835"
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="074d9-102">Hello World 自訂活動</span><span class="sxs-lookup"><span data-stu-id="074d9-102">Hello World Custom Activity</span></span>
<span data-ttu-id="074d9-103">這個範例會示範數個關鍵功能的 Windows Workflow Foundation (WF)，包括如何建立簡單的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="074d9-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="074d9-104">這個範例中示範的部分功能是以 C# 建立自訂活動，以及使用 `in` 和 `out` 引數 (<xref:System.Activities.InArgument> 和 <xref:System.Activities.OutArgument>)。</span><span class="sxs-lookup"><span data-stu-id="074d9-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="074d9-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="074d9-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="074d9-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="074d9-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="074d9-107">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="074d9-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="074d9-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="074d9-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="074d9-109">以程式碼建立工作流程</span><span class="sxs-lookup"><span data-stu-id="074d9-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="074d9-110">在這個範例中，會使用 C# 程式碼建立兩個自訂活動。</span><span class="sxs-lookup"><span data-stu-id="074d9-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="074d9-111">這兩個自訂活動直接或間接繼承自 <xref:System.Activities.Activity%601>，以傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="074d9-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="074d9-112">使用泛型傳回值 (而不繼承自非泛型 <xref:System.Activities.Activity> 類別) 的好處是，某些活動 (例如 <xref:System.Activities.Statements.Assign>) 在當做複合活動的一部分使用時能夠存取傳回值。</span><span class="sxs-lookup"><span data-stu-id="074d9-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="074d9-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="074d9-113">AppendString</span></span>  
 <span data-ttu-id="074d9-114">這個活動繼承自 <xref:System.Activities.Activity%601>，會使用串連兩個字串的 <xref:System.Activities.Statements.Assign> 活動。</span><span class="sxs-lookup"><span data-stu-id="074d9-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="074d9-115">Prepend String</span><span class="sxs-lookup"><span data-stu-id="074d9-115">Prepend String</span></span>  
 <span data-ttu-id="074d9-116">這個活動直接繼承自 <xref:System.Activities.CodeActivity%601>，會建立與 `AppendString` 活動類似的功能，即使用程式碼中實作的邏輯，而不是包含既有的活動。</span><span class="sxs-lookup"><span data-stu-id="074d9-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="074d9-117">下列檔案包含在此專案中。</span><span class="sxs-lookup"><span data-stu-id="074d9-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="074d9-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="074d9-118">AppendString.cs</span></span>  
 <span data-ttu-id="074d9-119">附加字串的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="074d9-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="074d9-120">它會採用在字串中，並將它與結合常值文字字串"says hello world"以形成完整訊息做為輸出。</span><span class="sxs-lookup"><span data-stu-id="074d9-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="074d9-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="074d9-121">PrependString.cs</span></span>  
 <span data-ttu-id="074d9-122">這個活動會將預先定義的字串前置到輸入字串。</span><span class="sxs-lookup"><span data-stu-id="074d9-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="074d9-123">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="074d9-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="074d9-124">使用 `AppendString` 和 `PrependString` 自訂活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="074d9-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="074d9-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="074d9-125">Program.cs</span></span>  
 <span data-ttu-id="074d9-126">執行工作流程的程式。</span><span class="sxs-lookup"><span data-stu-id="074d9-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="074d9-127">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="074d9-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="074d9-128">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 HelloWorld.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="074d9-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="074d9-129">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="074d9-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="074d9-130">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="074d9-130">To run the solution, press F5.</span></span>