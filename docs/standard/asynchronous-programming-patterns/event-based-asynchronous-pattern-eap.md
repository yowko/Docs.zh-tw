---
title: 事件架構非同步模式 (EAP)
description: 請參閱 .NET 中以事件為基礎之非同步模式（EAP）的相關文章連結，例如執行、最佳作法、實施 EAP 用戶端等等。
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 03b4d914d72b96b882c774565654c022b145b5f2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768868"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="3e6cf-103">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="3e6cf-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="3e6cf-104">將非同步功能公開到用戶端程式碼的方式有許多種；</span><span class="sxs-lookup"><span data-stu-id="3e6cf-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="3e6cf-105">事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e6cf-106">從 .NET Framework 4 開始，工作平行程式庫會為非同步處理和平行程式設計提供新的模型。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-106">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="3e6cf-107">如需詳細資訊，請參閱工作[平行程式庫（TPL）](../parallel-programming/task-parallel-library-tpl.md)和以工作[為基礎的非同步模式（](task-based-asynchronous-pattern-tap.md)點一下）。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="3e6cf-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e6cf-108">In This Section</span></span>

 [<span data-ttu-id="3e6cf-109">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="3e6cf-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="3e6cf-110">描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="3e6cf-111">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="3e6cf-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-112">描述將具有非同步功能的類別封裝起來的標準化方式。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="3e6cf-113">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3e6cf-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-114">描述根據事件架構非同步模式來公開非同步功能的需求。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="3e6cf-115">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="3e6cf-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-116">描述如何判斷何時應選擇實作事件架構非同步模式，而非由[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md) 所代表的 <xref:System.IAsyncResult> 模式</span><span class="sxs-lookup"><span data-stu-id="3e6cf-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="3e6cf-117">如何：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="3e6cf-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-118">描述如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="3e6cf-119">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="3e6cf-120">操作說明：實作事件架構非同步模式的用戶端</span><span class="sxs-lookup"><span data-stu-id="3e6cf-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-121">描述如何建立使用實作事件架構非同步模式之元件的用戶端。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="3e6cf-122">如何：使用支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="3e6cf-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="3e6cf-123">描述如何使用可支援事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e6cf-124">參考</span><span class="sxs-lookup"><span data-stu-id="3e6cf-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="3e6cf-125">描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="3e6cf-126">描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="3e6cf-127">描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e6cf-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="3e6cf-128">Related Sections</span></span>

 [<span data-ttu-id="3e6cf-129">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="3e6cf-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="3e6cf-130">描述非同步處理和平行作業的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="3e6cf-131">執行緒</span><span class="sxs-lookup"><span data-stu-id="3e6cf-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="3e6cf-132">說明 .NET 中的多執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="3e6cf-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6cf-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e6cf-133">See also</span></span>

- [<span data-ttu-id="3e6cf-134">受控執行緒最佳做法</span><span class="sxs-lookup"><span data-stu-id="3e6cf-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="3e6cf-135">事件</span><span class="sxs-lookup"><span data-stu-id="3e6cf-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="3e6cf-136">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="3e6cf-136">Asynchronous Programming Design Patterns</span></span>](index.md)
