---
title: "內建活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31e1b8c2-7f74-458a-b2e2-fddc5b10eac1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 642ba5100cca17623a07e5de613b6d6aa26bd23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="built-in-activities"></a><span data-ttu-id="0354c-102">內建活動</span><span class="sxs-lookup"><span data-stu-id="0354c-102">Built-in Activities</span></span>
<span data-ttu-id="0354c-103">本節包含的範例會示範內建的 [!INCLUDE[wf](../../../../includes/wf-md.md)] 活動。</span><span class="sxs-lookup"><span data-stu-id="0354c-103">This section contains samples that demonstrate built-in [!INCLUDE[wf](../../../../includes/wf-md.md)] activities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0354c-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="0354c-104">In This Section</span></span>  
 [<span data-ttu-id="0354c-105">錯誤處理流程圖活動使用 TryCatch</span><span class="sxs-lookup"><span data-stu-id="0354c-105">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
 <span data-ttu-id="0354c-106">示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="0354c-106">Demonstrates how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 [<span data-ttu-id="0354c-107">一段中的模擬中斷活動</span><span class="sxs-lookup"><span data-stu-id="0354c-107">Emulating breaking in a While activity</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/emulating-breaking-in-a-while-activity.md)  
 <span data-ttu-id="0354c-108">示範如何中斷下列活動的迴圈機制：<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="0354c-108">Demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 [<span data-ttu-id="0354c-109">DynamicActivity 建立</span><span class="sxs-lookup"><span data-stu-id="0354c-109">DynamicActivity Creation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)  
 <span data-ttu-id="0354c-110">示範在執行階段使用 <xref:System.Activities.DynamicActivity> 活動建立活動的兩種不同方式。</span><span class="sxs-lookup"><span data-stu-id="0354c-110">Demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 [<span data-ttu-id="0354c-111">搭配.NET Framework 3.5 Ruleset 使用變數</span><span class="sxs-lookup"><span data-stu-id="0354c-111">Using Variables with a .NET Framework 3.5 Ruleset</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-variables-with-dotnet-ruleset.md)  
 <span data-ttu-id="0354c-112">示範如何建立使用 <xref:System.Activities.Statements.Interop> 活動整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中使用原則和規則所撰寫自訂活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="0354c-112">Demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span>  
  
 [<span data-ttu-id="0354c-113">從 XAML 載入</span><span class="sxs-lookup"><span data-stu-id="0354c-113">Load From XAML</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/load-from-xaml.md)  
 <span data-ttu-id="0354c-114">示範如何動態載入 XAML 工作流程，而不必執行 XamlBuildTask 工具。</span><span class="sxs-lookup"><span data-stu-id="0354c-114">Demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span>  
  
 [<span data-ttu-id="0354c-115">使用集合活動</span><span class="sxs-lookup"><span data-stu-id="0354c-115">Using Collection Activities</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-collection-activities.md)  
 <span data-ttu-id="0354c-116">示範如何透過實作 <xref:System.Activities.Statements.AddToCollection%601> 介面的類別使用集合活動 (<xref:System.Activities.Statements.ClearCollection%601>、<xref:System.Activities.Statements.ExistsInCollection%601>、<xref:System.Activities.Statements.RemoveFromCollection%601> 和 <xref:System.Collections.ICollection>)，以及如何建立逐一查看集合以列印出集合中每一個項目內容的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="0354c-116">Demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span>  
  
 [<span data-ttu-id="0354c-117">使用 InvokeMethod 活動</span><span class="sxs-lookup"><span data-stu-id="0354c-117">Using the InvokeMethod Activity</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-the-invokemethod-activity.md)  
 <span data-ttu-id="0354c-118">示範如何使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用公用類別中的公用方法。</span><span class="sxs-lookup"><span data-stu-id="0354c-118">Demonstrates how to use the <xref:System.Activities.Statements.InvokeMethod> activity to invoke public methods in public classes.</span></span>  
  
 [<span data-ttu-id="0354c-119">使用 Pick 活動</span><span class="sxs-lookup"><span data-stu-id="0354c-119">Using the Pick Activity</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
 <span data-ttu-id="0354c-120">示範如何使用 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="0354c-120">Demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 [<span data-ttu-id="0354c-121">使用程序性活動</span><span class="sxs-lookup"><span data-stu-id="0354c-121">Using Procedural Activities</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
 <span data-ttu-id="0354c-122">示範如何使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.WriteLine> 活動實作猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="0354c-122">Demonstrates how to use the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span>  
  
 [<span data-ttu-id="0354c-123">使用 CancellationScope</span><span class="sxs-lookup"><span data-stu-id="0354c-123">Using CancellationScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/using-cancellationscope.md)  
 <span data-ttu-id="0354c-124">示範如何使用 <xref:System.Activities.Statements.CancellationScope> 活動取消應用程式中的工作。</span><span class="sxs-lookup"><span data-stu-id="0354c-124">Demonstrates how to use the <xref:System.Activities.Statements.CancellationScope> activity to cancel work in an application.</span></span>  
  
 [<span data-ttu-id="0354c-125">叫用方法</span><span class="sxs-lookup"><span data-stu-id="0354c-125">InvokeMethod</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
 <span data-ttu-id="0354c-126">示範以不同的方式使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用類別的方法。</span><span class="sxs-lookup"><span data-stu-id="0354c-126">Demonstrates the different ways to use the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 [<span data-ttu-id="0354c-127">使用自訂類型之切換活動的使用方式</span><span class="sxs-lookup"><span data-stu-id="0354c-127">Usage of the Switch Activity with Custom Types</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/usage-of-the-switch-activity-with-custom-types.md)  
 <span data-ttu-id="0354c-128">描述如何啟用 <xref:System.Activities.Statements.Switch%601> 活動，在執行階段評估使用者定義的複雜類型。</span><span class="sxs-lookup"><span data-stu-id="0354c-128">Describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span>  
  
 [<span data-ttu-id="0354c-129">Interop 和 3.5 規則集</span><span class="sxs-lookup"><span data-stu-id="0354c-129">Interop with 3.5 Rule Set</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/interop-with-3-5-rule-set.md)  
 <span data-ttu-id="0354c-130">示範使用 <xref:System.Activities.Statements.Interop> 活動透過 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 和規則整合 <xref:System.Workflow.Activities.PolicyActivity> 中的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="0354c-130">Demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <xref:System.Workflow.Activities.PolicyActivity> and rules.</span></span>
