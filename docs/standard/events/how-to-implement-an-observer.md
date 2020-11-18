---
title: 如何：實作觀察器
description: 在 .NET 中執行觀察者。 觀察者設計模式需要觀察者之間的部門，以註冊通知和提供者。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET], observer design pattern
- observer design pattern [.NET], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: bfd595cec8e499b760f75f614bd0a61b031eb207
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828331"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="d8693-104">如何：實作觀察器</span><span class="sxs-lookup"><span data-stu-id="d8693-104">How to: Implement an Observer</span></span>
<span data-ttu-id="d8693-105">觀察者設計模式需要觀察者和提供者之間的分區，其中觀察者會註冊通知，而提供者會監視資料並將通知傳送到一個或多個觀察者。</span><span class="sxs-lookup"><span data-stu-id="d8693-105">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="d8693-106">本主題討論如何建立觀察者。</span><span class="sxs-lookup"><span data-stu-id="d8693-106">This topic discusses how to create an observer.</span></span> <span data-ttu-id="d8693-107">相關主題為[操作說明：實作提供者](how-to-implement-a-provider.md)，討論如何建立提供者。</span><span class="sxs-lookup"><span data-stu-id="d8693-107">A related topic, [How to: Implement a Provider](how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="d8693-108">建立觀察者</span><span class="sxs-lookup"><span data-stu-id="d8693-108">To create an observer</span></span>  
  
1. <span data-ttu-id="d8693-109">定義觀察者，這是實作 <xref:System.IObserver%601?displayProperty=nameWithType> 介面的型別。</span><span class="sxs-lookup"><span data-stu-id="d8693-109">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d8693-110">例如，下列程式碼定義名為 `TemperatureReporter` 的型別，它是包含 `Temperature` 泛型型別引數的建構 <xref:System.IObserver%601?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="d8693-110">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="d8693-111">如果觀察者可以在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作之前停止接收通知，請定義會保留由提供者的 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法傳回之 <xref:System.IDisposable> 實作的私用變數。</span><span class="sxs-lookup"><span data-stu-id="d8693-111">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d8693-112">您也應該定義訂閱方法，它會呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法並儲存傳回的 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="d8693-112">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="d8693-113">例如，下列的程式碼定義名為 `unsubscriber` 的私用變數，並定義呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法之 `Subscribe` 方法，然後將傳回的物件指派到 `unsubscriber` 變數。</span><span class="sxs-lookup"><span data-stu-id="d8693-113">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="d8693-114">定義讓觀察者能夠在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作之前停止接收通知的方法 (如果需要此功能)。</span><span class="sxs-lookup"><span data-stu-id="d8693-114">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="d8693-115">下列範例定義 `Unsubscribe` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8693-115">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="d8693-116">提供 <xref:System.IObserver%601> 介面定義的三個方法之實作：<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>，<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d8693-116">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d8693-117">視提供者和應用程式需求而定，<xref:System.IObserver%601.OnError%2A> 和 <xref:System.IObserver%601.OnCompleted%2A> 方法可以是虛設常式實作。</span><span class="sxs-lookup"><span data-stu-id="d8693-117">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="d8693-118">請注意，<xref:System.IObserver%601.OnError%2A> 方法不應將傳遞的 <xref:System.Exception> 物件當作例外狀況處理，而 <xref:System.IObserver%601.OnCompleted%2A> 方法可以自由呼叫提供者的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="d8693-118">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d8693-119">下列範例顯示 `TemperatureReporter` 類別的 <xref:System.IObserver%601> 實作。</span><span class="sxs-lookup"><span data-stu-id="d8693-119">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="d8693-120">範例</span><span class="sxs-lookup"><span data-stu-id="d8693-120">Example</span></span>  
 <span data-ttu-id="d8693-121">以下範例包含 `TemperatureReporter` 類別的完整原始程式碼，它提供溫度監視應用程式的 <xref:System.IObserver%601> 實作。</span><span class="sxs-lookup"><span data-stu-id="d8693-121">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d8693-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8693-122">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="d8693-123">觀察者設計模式</span><span class="sxs-lookup"><span data-stu-id="d8693-123">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="d8693-124">如何：執行提供者</span><span class="sxs-lookup"><span data-stu-id="d8693-124">How to: Implement a Provider</span></span>](how-to-implement-a-provider.md)
- [<span data-ttu-id="d8693-125">觀察器設計模式最佳作法</span><span class="sxs-lookup"><span data-stu-id="d8693-125">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
