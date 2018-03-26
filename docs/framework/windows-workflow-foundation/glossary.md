---
title: .NET Framework 4.5 的 Windows Workflow Foundation 字彙
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a0cc6d9a0c922e57bf00b649894f26b42a64f4
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a><span data-ttu-id="81309-102">.NET Framework 4.5 的 Windows Workflow Foundation 字彙</span><span class="sxs-lookup"><span data-stu-id="81309-102">Windows Workflow Foundation Glossary for .NET Framework 4.5</span></span>
<span data-ttu-id="81309-103">以下是 Windows Workflow Foundation 文件中使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="81309-103">The following terms are used in the Windows Workflow Foundation documentation.</span></span>  
  
## <a name="terms"></a><span data-ttu-id="81309-104">詞彙</span><span class="sxs-lookup"><span data-stu-id="81309-104">Terms</span></span>  
  
|<span data-ttu-id="81309-105">詞彙</span><span class="sxs-lookup"><span data-stu-id="81309-105">Term</span></span>|<span data-ttu-id="81309-106">定義</span><span class="sxs-lookup"><span data-stu-id="81309-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="81309-107">活動</span><span class="sxs-lookup"><span data-stu-id="81309-107">activity</span></span>|<span data-ttu-id="81309-108">Windows Workflow Foundation 中程式行為的單元。</span><span class="sxs-lookup"><span data-stu-id="81309-108">A unit of program behavior in Windows Workflow Foundation.</span></span> <span data-ttu-id="81309-109">可將單一活動組成更複雜的活動。</span><span class="sxs-lookup"><span data-stu-id="81309-109">Single activities can be composed together into more complex activities.</span></span>|  
|<span data-ttu-id="81309-110">Activity Action - 活動動作</span><span class="sxs-lookup"><span data-stu-id="81309-110">activity action</span></span>|<span data-ttu-id="81309-111">用來公開回呼以執行工作流程和活動的資料結構。</span><span class="sxs-lookup"><span data-stu-id="81309-111">A data structure used to expose callbacks for workflow and activity execution.</span></span>|  
|<span data-ttu-id="81309-112">Argument - 引數</span><span class="sxs-lookup"><span data-stu-id="81309-112">argument</span></span>|<span data-ttu-id="81309-113">定義進出活動的資料流程。</span><span class="sxs-lookup"><span data-stu-id="81309-113">Defines the data flow into and out of an activity.</span></span> <span data-ttu-id="81309-114">每個引數都有指定的方向：in、out 或 in/out。這些參數表示活動的輸入、輸出和輸入/輸出參數。</span><span class="sxs-lookup"><span data-stu-id="81309-114">Each argument has a specified direction: in, out, or in/out. These represent the input, output, and input/output parameters of the activity.</span></span>|  
|<span data-ttu-id="81309-115">Bookmark - 書籤</span><span class="sxs-lookup"><span data-stu-id="81309-115">bookmark</span></span>|<span data-ttu-id="81309-116">活動可暫停並等候繼續的時間點。</span><span class="sxs-lookup"><span data-stu-id="81309-116">The point at which an activity can pause and wait to be resumed.</span></span>|  
|<span data-ttu-id="81309-117">補償</span><span class="sxs-lookup"><span data-stu-id="81309-117">compensation</span></span>|<span data-ttu-id="81309-118">設計用來恢復或降低先前完成工作之影響的動作群組。</span><span class="sxs-lookup"><span data-stu-id="81309-118">A group of actions designed to undo or mitigate the effect of previously completed work.</span></span>|  
|<span data-ttu-id="81309-119">相互關聯</span><span class="sxs-lookup"><span data-stu-id="81309-119">correlation</span></span>|<span data-ttu-id="81309-120">路由傳送訊息至工作流程或服務執行個體的機制。</span><span class="sxs-lookup"><span data-stu-id="81309-120">The mechanism for routing messages to a workflow or service instance.</span></span>|  
|<span data-ttu-id="81309-121">運算式</span><span class="sxs-lookup"><span data-stu-id="81309-121">expression</span></span>|<span data-ttu-id="81309-122">接受一個或多個引數、在引數上執行作業並傳回單一值的建構。</span><span class="sxs-lookup"><span data-stu-id="81309-122">A construct that takes in one or more arguments, performs an operation on the arguments and returns a single value.</span></span> <span data-ttu-id="81309-123">只要可使用活動的任何地方，就可以使用運算式。</span><span class="sxs-lookup"><span data-stu-id="81309-123">Expressions can be used anywhere an activity can be used.</span></span>|  
|<span data-ttu-id="81309-124">Flowchart - 流程圖</span><span class="sxs-lookup"><span data-stu-id="81309-124">flowchart</span></span>|<span data-ttu-id="81309-125">將程式元件表示為符號並用方向箭頭加以連結的已知模型開發架構。</span><span class="sxs-lookup"><span data-stu-id="81309-125">A well-known modeling paradigm that represents program components as symbols linked together with directional arrows.</span></span>  <span data-ttu-id="81309-126">在 .NET Framework 4 中，工作流程可透過 Flowchart 活動模型化為流程圖。</span><span class="sxs-lookup"><span data-stu-id="81309-126">In the .NET Framework 4, workflows can be modeled as flowcharts using the Flowchart activity.</span></span>|  
|<span data-ttu-id="81309-127">Long-running Process - 長期執行的處理序</span><span class="sxs-lookup"><span data-stu-id="81309-127">long-running process</span></span>|<span data-ttu-id="81309-128">不會立即傳回、可跨越多次系統重新啟動的程式執行單元。</span><span class="sxs-lookup"><span data-stu-id="81309-128">A unit of program execution that does not return immediately and may span system restarts.</span></span>|  
|<span data-ttu-id="81309-129">保存性</span><span class="sxs-lookup"><span data-stu-id="81309-129">persistence</span></span>|<span data-ttu-id="81309-130">將工作流程或服務的狀態儲存至永久性媒體，使其得以從記憶體卸載或在系統失敗後復原。</span><span class="sxs-lookup"><span data-stu-id="81309-130">Saving the state of a workflow or service to a durable medium, so that it can be unloaded from memory or recovered after a system failure.</span></span>|  
|<span data-ttu-id="81309-131">State Machine - 狀態機器</span><span class="sxs-lookup"><span data-stu-id="81309-131">state machine</span></span>|<span data-ttu-id="81309-132">將程式元件表示為個別狀態並用事件驅動狀態轉換加以連結的已知模型開發架構。</span><span class="sxs-lookup"><span data-stu-id="81309-132">A well-known modeling paradigm that represents program components as individual states linked together with event-driven state transitions.</span></span>  <span data-ttu-id="81309-133">工作流程可透過 StateMachine 活動模型化為狀態機器。</span><span class="sxs-lookup"><span data-stu-id="81309-133">Workflows can be modeled as state machines using the StateMachine activity.</span></span>|  
|<span data-ttu-id="81309-134">Substance - 令重</span><span class="sxs-lookup"><span data-stu-id="81309-134">substance</span></span>|<span data-ttu-id="81309-135">表示在通用識別項下的相關書籤群組，允許執行階段決定特定書籤的繼續執行是否有效或可變成有效。</span><span class="sxs-lookup"><span data-stu-id="81309-135">Represents a group of related bookmarks under a common identifier and allows the runtime to make decisions about whether a particular bookmark resumption is valid or may become valid.</span></span>|  
|<span data-ttu-id="81309-136">Type Converter - 型別轉換子</span><span class="sxs-lookup"><span data-stu-id="81309-136">type converter</span></span>|<span data-ttu-id="81309-137">CLR 型別可以與一個或多個 System.ComponentModel.TypeConverter 衍生型別相關聯，這些型別可將 CLR 型別的執行個體和其他型別的執行個體來回轉換。</span><span class="sxs-lookup"><span data-stu-id="81309-137">A CLR type can be associated with one or more System.ComponentModel.TypeConverter derived types that enable converting instances of the CLR type to and from instances of other types.</span></span> <span data-ttu-id="81309-138">型別轉換子透過 System.ComponentModel.TypeConverterAttribute 屬性來與 CLR 型別相關聯。</span><span class="sxs-lookup"><span data-stu-id="81309-138">A type converterr is associated with a CLR type using the System.ComponentModel.TypeConverterAttribute attribute.</span></span>  <span data-ttu-id="81309-139">TypeConverterAttribute 可直接在 CLR 型別或在屬性上指定。</span><span class="sxs-lookup"><span data-stu-id="81309-139">A TypeConverterAttribute can be specified directly on the CLR type or on a property.</span></span> <span data-ttu-id="81309-140">屬性上指定之型別轉換子的優先順序永遠高於屬性之 CLR 型別上指定之型別轉換子。</span><span class="sxs-lookup"><span data-stu-id="81309-140">A type converter specified on a property always takes precedence over a type converter specified on the CLR type of the property.</span></span>|  
|<span data-ttu-id="81309-141">變數</span><span class="sxs-lookup"><span data-stu-id="81309-141">variable</span></span>|<span data-ttu-id="81309-142">表示必須儲存以供稍後存取之部分資料的儲存體。</span><span class="sxs-lookup"><span data-stu-id="81309-142">Represents the storage of some data that must be saved and accessed later.</span></span>|  
|<span data-ttu-id="81309-143">工作流程</span><span class="sxs-lookup"><span data-stu-id="81309-143">workflow</span></span>|<span data-ttu-id="81309-144">主機處理序所叫用之單一活動或活動樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="81309-144">A single activity or tree of activities invoked by a host process.</span></span>|  
|<span data-ttu-id="81309-145">XAML</span><span class="sxs-lookup"><span data-stu-id="81309-145">XAML</span></span>|<span data-ttu-id="81309-146">eXtensible Application Markup Language</span><span class="sxs-lookup"><span data-stu-id="81309-146">eXtensible Application Markup Language</span></span>|
