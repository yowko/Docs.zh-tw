---
title: 事件架構非同步模式 (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be4935d74affa227386aa6c63dad13e7e2f7d3dd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207452"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="af8f3-102">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="af8f3-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="af8f3-103">將非同步功能公開到用戶端程式碼的方式有許多種；</span><span class="sxs-lookup"><span data-stu-id="af8f3-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="af8f3-104">事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。</span><span class="sxs-lookup"><span data-stu-id="af8f3-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af8f3-105">從 .NET Framework 4 開始，工作平行程式庫會為非同步處理和平行程式設計提供新的模型。</span><span class="sxs-lookup"><span data-stu-id="af8f3-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="af8f3-106">如需詳細資訊，請參閱 [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) 和 [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f3-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="af8f3-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="af8f3-107">In This Section</span></span>

 [<span data-ttu-id="af8f3-108">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="af8f3-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="af8f3-109">描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="af8f3-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="af8f3-110">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="af8f3-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-111">描述將具有非同步功能的類別封裝起來的標準化方式。</span><span class="sxs-lookup"><span data-stu-id="af8f3-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="af8f3-112">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="af8f3-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-113">描述根據事件架構非同步模式來公開非同步功能的需求。</span><span class="sxs-lookup"><span data-stu-id="af8f3-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="af8f3-114">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="af8f3-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-115">描述如何判斷何時應選擇實作事件架構非同步模式，而非由[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md) 所代表的 <xref:System.IAsyncResult> 模式</span><span class="sxs-lookup"><span data-stu-id="af8f3-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="af8f3-116">操作說明：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="af8f3-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-117">描述如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="af8f3-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="af8f3-118">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。</span><span class="sxs-lookup"><span data-stu-id="af8f3-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="af8f3-119">操作說明：實作事件架構非同步模式的用戶端</span><span class="sxs-lookup"><span data-stu-id="af8f3-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-120">描述如何建立使用實作事件架構非同步模式之元件的用戶端。</span><span class="sxs-lookup"><span data-stu-id="af8f3-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="af8f3-121">操作說明：使用支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="af8f3-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="af8f3-122">描述如何使用可支援事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="af8f3-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="af8f3-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="af8f3-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="af8f3-124">描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="af8f3-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="af8f3-125">描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="af8f3-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="af8f3-126">描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="af8f3-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af8f3-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="af8f3-127">Related Sections</span></span>

 [<span data-ttu-id="af8f3-128">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="af8f3-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="af8f3-129">描述非同步處理和平行作業的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="af8f3-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="af8f3-130">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="af8f3-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="af8f3-131">說明 .NET 中的多執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="af8f3-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8f3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af8f3-132">See also</span></span>

- [<span data-ttu-id="af8f3-133">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="af8f3-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)  
- [<span data-ttu-id="af8f3-134">事件</span><span class="sxs-lookup"><span data-stu-id="af8f3-134">Events</span></span>](../events/index.md)  
- [<span data-ttu-id="af8f3-135">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="af8f3-135">Asynchronous Programming Design Patterns</span></span>](index.md)
