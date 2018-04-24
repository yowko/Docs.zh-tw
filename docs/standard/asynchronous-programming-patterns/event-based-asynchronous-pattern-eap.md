---
title: 事件架構非同步模式 (EAP)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: 20
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fecd71355d53f1e3937d3724569b10fa0c8e50da
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="70053-102">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="70053-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="70053-103">將非同步功能公開到用戶端程式碼的方式有許多種；</span><span class="sxs-lookup"><span data-stu-id="70053-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="70053-104">事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。</span><span class="sxs-lookup"><span data-stu-id="70053-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70053-105">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，工作平行程式庫會為非同步處理和平行程式設計提供新的模型。</span><span class="sxs-lookup"><span data-stu-id="70053-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="70053-106">如需詳細資訊，請參閱[平行程式設計](../../../docs/standard/parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="70053-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70053-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="70053-107">In This Section</span></span>  
 [<span data-ttu-id="70053-108">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="70053-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="70053-109">描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="70053-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="70053-110">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="70053-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="70053-111">描述將具有非同步功能的類別封裝起來的標準化方式。</span><span class="sxs-lookup"><span data-stu-id="70053-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="70053-112">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="70053-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="70053-113">描述根據事件架構非同步模式來公開非同步功能的需求。</span><span class="sxs-lookup"><span data-stu-id="70053-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="70053-114">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="70053-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="70053-115">描述如何判斷何時應該選擇實作事件架構非同步模式，而不是 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="70053-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="70053-116">逐步解說：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="70053-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="70053-117">說明如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="70053-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="70053-118">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。</span><span class="sxs-lookup"><span data-stu-id="70053-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="70053-119">操作說明：使用支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="70053-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="70053-120">描述如何使用可支援事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="70053-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70053-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="70053-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="70053-122">描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="70053-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="70053-123">描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="70053-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="70053-124">描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="70053-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70053-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="70053-125">Related Sections</span></span>  
 [<span data-ttu-id="70053-126">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="70053-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="70053-127">描述非同步處理和平行作業的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="70053-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="70053-128">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="70053-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="70053-129">說明在 .NET Framework 的多執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="70053-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="70053-130">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="70053-130">Threading</span></span>](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="70053-131">說明 C# 和 Visual Basic 語言的多執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="70053-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70053-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="70053-132">See Also</span></span>  
 [<span data-ttu-id="70053-133">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="70053-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="70053-134">事件</span><span class="sxs-lookup"><span data-stu-id="70053-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="70053-135">元件中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="70053-135">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="70053-136">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="70053-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
