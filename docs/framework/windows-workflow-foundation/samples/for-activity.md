---
title: 針對活動
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881517"
---
# <a name="for-activity"></a><span data-ttu-id="243bf-102">針對活動</span><span class="sxs-lookup"><span data-stu-id="243bf-102">For Activity</span></span>
<span data-ttu-id="243bf-103">For 範例示範如何建置繼承自 <xref:System.Activities.NativeActivity> 的自訂活動，以及在工作流程中使用它來執行真實的範例。</span><span class="sxs-lookup"><span data-stu-id="243bf-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="243bf-104">本範例中包含的自訂活動作用就像 C# `for` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="243bf-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="243bf-105">T</span><span class="sxs-lookup"><span data-stu-id="243bf-105">T</span></span>  
  
 <span data-ttu-id="243bf-106">`For` 自訂活動擁有名為 `InitAction`、`IterationAction`、`Condition` 和 `Body` 的屬性，這些屬性分別對應至標準 C# `For` 陳述式中的初始化陳述式、反覆性陳述式、持續條件以及主體陳述式。</span><span class="sxs-lookup"><span data-stu-id="243bf-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="243bf-107">下表描述範例中的重要檔案。</span><span class="sxs-lookup"><span data-stu-id="243bf-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="243bf-108">檔案</span><span class="sxs-lookup"><span data-stu-id="243bf-108">File</span></span>|<span data-ttu-id="243bf-109">描述</span><span class="sxs-lookup"><span data-stu-id="243bf-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="243bf-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="243bf-110">For.cs</span></span>|<span data-ttu-id="243bf-111">`For` 自訂活動的類別定義，它會擴充 <xref:System.Activities.NativeActivity> 類別以提供 C# `For` 陳述式的功能。</span><span class="sxs-lookup"><span data-stu-id="243bf-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="243bf-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="243bf-112">Program.cs</span></span>|<span data-ttu-id="243bf-113">用戶端應用程式，它會使用自訂 `For` 活動執行集合上基本的反覆性工作。</span><span class="sxs-lookup"><span data-stu-id="243bf-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="243bf-114">使用 `For` 自訂活動時，務必確定已設定 `Condition` 屬性，否則可能發生無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="243bf-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="243bf-115">示範</span><span class="sxs-lookup"><span data-stu-id="243bf-115">Demonstrates</span></span>  
 <span data-ttu-id="243bf-116">建立繼承自 <xref:System.Activities.NativeActivity> 的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="243bf-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="243bf-117">討論</span><span class="sxs-lookup"><span data-stu-id="243bf-117">Discussion</span></span>  
 <span data-ttu-id="243bf-118">下表說明本範例中所包含活動的屬性。</span><span class="sxs-lookup"><span data-stu-id="243bf-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="243bf-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="243bf-119">InitAction</span></span>  
 <span data-ttu-id="243bf-120">初始化陳述式</span><span class="sxs-lookup"><span data-stu-id="243bf-120">Initialization statement</span></span>  
  
 <span data-ttu-id="243bf-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="243bf-121">IterationAction</span></span>  
 <span data-ttu-id="243bf-122">反覆性陳述式</span><span class="sxs-lookup"><span data-stu-id="243bf-122">Iterative statement</span></span>  
  
 <span data-ttu-id="243bf-123">條件</span><span class="sxs-lookup"><span data-stu-id="243bf-123">Condition</span></span>  
 <span data-ttu-id="243bf-124">持續陳述式</span><span class="sxs-lookup"><span data-stu-id="243bf-124">Continuation statement</span></span>  
  
 <span data-ttu-id="243bf-125">本文</span><span class="sxs-lookup"><span data-stu-id="243bf-125">Body</span></span>  
 <span data-ttu-id="243bf-126">主體陳述式</span><span class="sxs-lookup"><span data-stu-id="243bf-126">Body statement</span></span>  
  
 <span data-ttu-id="243bf-127">活動會繼承自 <xref:System.Activities.NativeActivity> 以便存取執行階段功能，例如排程執行其他活動、使用 `ScheduleActivity` 的其中一個 <xref:System.Activities.NativeActivityContext> 方法。</span><span class="sxs-lookup"><span data-stu-id="243bf-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="243bf-128">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="243bf-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="243bf-129">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [For.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="243bf-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="243bf-130">按 CTRL+SHIFT+B 以建置此方案。</span><span class="sxs-lookup"><span data-stu-id="243bf-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="243bf-131">按 F5 鍵執行方案。</span><span class="sxs-lookup"><span data-stu-id="243bf-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="243bf-132">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="243bf-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="243bf-133">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="243bf-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="243bf-134">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="243bf-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="243bf-135">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="243bf-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`