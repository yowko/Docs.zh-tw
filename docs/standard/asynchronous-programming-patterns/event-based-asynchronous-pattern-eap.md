---
title: 事件架構非同步模式 (EAP)
description: 請參閱 .NET 中事件架構非同步模式 (EAP) 的相關文章連結，例如執行、最佳作法、實行 EAP 用戶端等。
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 16aabeb55a56c63449a865d00044c463657de740
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888837"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="40742-103">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="40742-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="40742-104">將非同步功能公開到用戶端程式碼的方式有許多種；</span><span class="sxs-lookup"><span data-stu-id="40742-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="40742-105">事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。</span><span class="sxs-lookup"><span data-stu-id="40742-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40742-106">從 .NET Framework 4 開始，工作平行程式庫會為非同步和平行程式設計提供新的模型。</span><span class="sxs-lookup"><span data-stu-id="40742-106">Starting with .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="40742-107">如需詳細資訊，請參閱工作 [平行程式庫 (TPL) ](../parallel-programming/task-parallel-library-tpl.md) 和以工作 [為基礎的非同步模式 (請參閱) ](task-based-asynchronous-pattern-tap.md)。</span><span class="sxs-lookup"><span data-stu-id="40742-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="40742-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="40742-108">In This Section</span></span>

 [<span data-ttu-id="40742-109">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="40742-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="40742-110">描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="40742-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="40742-111">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="40742-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-112">描述將具有非同步功能的類別封裝起來的標準化方式。</span><span class="sxs-lookup"><span data-stu-id="40742-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="40742-113">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="40742-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-114">描述根據事件架構非同步模式來公開非同步功能的需求。</span><span class="sxs-lookup"><span data-stu-id="40742-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="40742-115">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="40742-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-116">描述如何判斷何時應選擇實作事件架構非同步模式，而非由[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md) 所代表的 <xref:System.IAsyncResult> 模式</span><span class="sxs-lookup"><span data-stu-id="40742-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="40742-117">作法：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="40742-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-118">描述如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="40742-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="40742-119">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。</span><span class="sxs-lookup"><span data-stu-id="40742-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="40742-120">作法：實作事件架構非同步模式的用戶端</span><span class="sxs-lookup"><span data-stu-id="40742-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-121">描述如何建立使用實作事件架構非同步模式之元件的用戶端。</span><span class="sxs-lookup"><span data-stu-id="40742-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="40742-122">作法：使用支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="40742-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="40742-123">描述如何使用可支援事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="40742-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="40742-124">參考</span><span class="sxs-lookup"><span data-stu-id="40742-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="40742-125">描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="40742-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="40742-126">描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="40742-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="40742-127">描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="40742-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40742-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="40742-128">Related Sections</span></span>

 [<span data-ttu-id="40742-129">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="40742-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="40742-130">描述非同步處理和平行作業的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="40742-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="40742-131">執行緒</span><span class="sxs-lookup"><span data-stu-id="40742-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="40742-132">說明 .NET 中的多執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="40742-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40742-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="40742-133">See also</span></span>

- [<span data-ttu-id="40742-134">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="40742-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="40742-135">事件</span><span class="sxs-lookup"><span data-stu-id="40742-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="40742-136">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="40742-136">Asynchronous Programming Design Patterns</span></span>](index.md)
