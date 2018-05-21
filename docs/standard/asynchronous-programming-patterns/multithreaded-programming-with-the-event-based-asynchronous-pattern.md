---
title: 使用事件架構非同步模式設計多執行緒程式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
ms.openlocfilehash: 26e555a158ced352c297952b56f7557cbd825cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="207f3-102">使用事件架構非同步模式設計多執行緒程式</span><span class="sxs-lookup"><span data-stu-id="207f3-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="207f3-103">將非同步功能公開到用戶端程式碼的方式有許多種；</span><span class="sxs-lookup"><span data-stu-id="207f3-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="207f3-104">事件架構非同步模式會針對要呈現非同步行為之類別指示建議的方法。</span><span class="sxs-lookup"><span data-stu-id="207f3-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="207f3-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="207f3-105">In This Section</span></span>  
 [<span data-ttu-id="207f3-106">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="207f3-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="207f3-107">描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="207f3-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="207f3-108">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="207f3-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="207f3-109">描述將具有非同步功能的類別封裝起來的標準化方式。</span><span class="sxs-lookup"><span data-stu-id="207f3-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="207f3-110">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="207f3-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="207f3-111">描述根據事件架構非同步模式來公開非同步功能的需求。</span><span class="sxs-lookup"><span data-stu-id="207f3-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="207f3-112">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="207f3-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="207f3-113">描述如何判斷何時應該選擇實作事件架構非同步模式，而不是 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="207f3-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="207f3-114">逐步解說：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="207f3-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="207f3-115">說明如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="207f3-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="207f3-116">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。</span><span class="sxs-lookup"><span data-stu-id="207f3-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="207f3-117">操作說明：使用支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="207f3-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="207f3-118">描述如何使用可支援事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="207f3-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="207f3-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="207f3-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="207f3-120">描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="207f3-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="207f3-121">描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="207f3-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="207f3-122">描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。</span><span class="sxs-lookup"><span data-stu-id="207f3-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207f3-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="207f3-123">See Also</span></span>  
 [<span data-ttu-id="207f3-124">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="207f3-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="207f3-125">事件</span><span class="sxs-lookup"><span data-stu-id="207f3-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="207f3-126">元件中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="207f3-126">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="207f3-127">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="207f3-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
