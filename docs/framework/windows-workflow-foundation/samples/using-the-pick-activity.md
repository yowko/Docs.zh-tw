---
title: 使用 Pick 活動
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004727"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="01d87-102">使用 Pick 活動</span><span class="sxs-lookup"><span data-stu-id="01d87-102">Using the Pick Activity</span></span>
<span data-ttu-id="01d87-103">這個範例示範如何使用 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="01d87-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="01d87-104"><xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制模型。</span><span class="sxs-lookup"><span data-stu-id="01d87-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="01d87-105">其行為與 C# `switch` 陳述式類似，只執行 `switch` 陳述式的其中一個分支。</span><span class="sxs-lookup"><span data-stu-id="01d87-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="01d87-106">不同於 `switch` 陳述式是根據值來執行分支，<xref:System.Activities.Statements.Pick> 活動是根據活動完成方式來執行分支。</span><span class="sxs-lookup"><span data-stu-id="01d87-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="01d87-107">這個範例會提示使用者在主控台於給定時限內輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="01d87-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="01d87-108">範例中的 <xref:System.Activities.Statements.Pick> 活動有兩個分支，它們是根據使用者是否在 5 秒內輸入名稱來執行。</span><span class="sxs-lookup"><span data-stu-id="01d87-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="01d87-109">如果使用者在 5 秒內輸入名稱，則會執行包含自訂 `ReadLine` 活動的第一個分支，否則會執行包含 <xref:System.Activities.Statements.Delay> 活動的另一個分支。</span><span class="sxs-lookup"><span data-stu-id="01d87-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="01d87-110">在主控台輸入使用者名稱後，就會在主控台上列印此名稱。</span><span class="sxs-lookup"><span data-stu-id="01d87-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="01d87-111">如果沒有在 5 秒內輸入，則作業逾時。</span><span class="sxs-lookup"><span data-stu-id="01d87-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="01d87-112">示範</span><span class="sxs-lookup"><span data-stu-id="01d87-112">Demonstrates</span></span>
 <span data-ttu-id="01d87-113"><xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="01d87-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="01d87-114">討論</span><span class="sxs-lookup"><span data-stu-id="01d87-114">Discussion</span></span>
 <span data-ttu-id="01d87-115">此範例包含設計工具工作流程和程式碼工作流程。</span><span class="sxs-lookup"><span data-stu-id="01d87-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="01d87-116">設計工具的工作流程設計工具版本的範例示範如何建立工作流程設計工具中。</span><span class="sxs-lookup"><span data-stu-id="01d87-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="01d87-117">包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="01d87-117">The following files are included:</span></span>

- <span data-ttu-id="01d87-118">Program.cs:包含`Main`執行範例工作流程函式。</span><span class="sxs-lookup"><span data-stu-id="01d87-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="01d87-119">ReadString.cs:從主控台讀取輸入的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="01d87-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="01d87-120">Sequence1.xaml:使用 Pick 的設計工具中建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="01d87-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="01d87-121">自動程式化的工作流程範例的程式碼版本示範如何建立工作流程設計工具中。</span><span class="sxs-lookup"><span data-stu-id="01d87-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="01d87-122">包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="01d87-122">The following files are included:</span></span>

- <span data-ttu-id="01d87-123">Program.cs:包含`Main`執行範例工作流程函式。</span><span class="sxs-lookup"><span data-stu-id="01d87-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="01d87-124">ReadString.cs:從主控台讀取輸入的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="01d87-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="01d87-125">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="01d87-125">To use this sample</span></span>

1. <span data-ttu-id="01d87-126">使用 Visual Studio 2010 開啟 Pick.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="01d87-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="01d87-127">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="01d87-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="01d87-128">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="01d87-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="01d87-129">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="01d87-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01d87-130">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="01d87-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="01d87-131">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="01d87-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01d87-132">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="01d87-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`