---
title: HOW TO：實作提供者
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eecf16625c20ad5ff89791e221a4a40b2777956b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543785"
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="19221-102">HOW TO：實作提供者</span><span class="sxs-lookup"><span data-stu-id="19221-102">How to: Implement a Provider</span></span>
<span data-ttu-id="19221-103">觀察者設計模式需要提供者和一個或多個觀察者之間的分區，其中提供者會監視資料並傳送通知，而觀察者會接收來自提供者的通知 (回呼)。</span><span class="sxs-lookup"><span data-stu-id="19221-103">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="19221-104">本主題討論如何建立提供者。</span><span class="sxs-lookup"><span data-stu-id="19221-104">This topic discusses how to create a provider.</span></span> <span data-ttu-id="19221-105">相關主題為[如何：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)，討論如何建立觀察者。</span><span class="sxs-lookup"><span data-stu-id="19221-105">A related topic, [How to: Implement an Observer](../../../docs/standard/events/how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="19221-106">建立提供者</span><span class="sxs-lookup"><span data-stu-id="19221-106">To create a provider</span></span>  
  
1.  <span data-ttu-id="19221-107">定義提供者負責傳送給觀察者的資料。</span><span class="sxs-lookup"><span data-stu-id="19221-107">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="19221-108">雖然提供者和它傳送給觀察者的資料可以是單一的型別，但它們通常以不同型別代表。</span><span class="sxs-lookup"><span data-stu-id="19221-108">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="19221-109">例如，在溫度監控應用程式中，`Temperature` 結構定義的提供者 (在下一步中以 `TemperatureMonitor` 代表) 監視並由觀察者訂閱的資料。</span><span class="sxs-lookup"><span data-stu-id="19221-109">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  <span data-ttu-id="19221-110">定義資料提供者，這是實作 <xref:System.IObservable%601?displayProperty=nameWithType> 介面的型別。</span><span class="sxs-lookup"><span data-stu-id="19221-110">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="19221-111">提供者的泛型型別引數是提供者傳送給觀察者的型別。</span><span class="sxs-lookup"><span data-stu-id="19221-111">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="19221-112">下列範例會定義 `TemperatureMonitor` 類別，這是包含泛型型別引數 `Temperature` 的建構 <xref:System.IObservable%601?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="19221-112">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  <span data-ttu-id="19221-113">決定提供者儲存對觀察者的參考之方式，讓每個觀察者在適當時被通知。</span><span class="sxs-lookup"><span data-stu-id="19221-113">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="19221-114">大多數情況下，如泛型 <xref:System.Collections.Generic.List%601> 物件等集合物件用於此用途。</span><span class="sxs-lookup"><span data-stu-id="19221-114">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="19221-115">下列範例定義在 `TemperatureMonitor` 中具現化的私用 <xref:System.Collections.Generic.List%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="19221-115">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  <span data-ttu-id="19221-116">定義提供者可傳回到訂閱者的 <xref:System.IDisposable> 實作，讓它們可隨時停止接收通知。</span><span class="sxs-lookup"><span data-stu-id="19221-116">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="19221-117">下列範例定義巢狀 `Unsubscriber` 類別，它在類別初始化時將參考傳遞到訂閱者集合及訂閱者。</span><span class="sxs-lookup"><span data-stu-id="19221-117">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="19221-118">此程式碼讓訂閱者能夠呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作，以將自己從訂閱者集合移除。</span><span class="sxs-lookup"><span data-stu-id="19221-118">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <span data-ttu-id="19221-119">實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="19221-119">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="19221-120">該方法傳遞參考到 <xref:System.IObserver%601?displayProperty=nameWithType> 介面，並應該儲存在步驟 3 中為該目的而設計的物件中。</span><span class="sxs-lookup"><span data-stu-id="19221-120">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="19221-121">這個方法應再傳回在步驟 4 中開發的 <xref:System.IDisposable> 實作。</span><span class="sxs-lookup"><span data-stu-id="19221-121">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="19221-122">下列範例顯示 `TemperatureMonitor` 類別中 <xref:System.IObservable%601.Subscribe%2A> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="19221-122">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  <span data-ttu-id="19221-123">藉由呼叫觀察者的 <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作，以適時通知它們。</span><span class="sxs-lookup"><span data-stu-id="19221-123">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="19221-124">在某些情況下，當錯誤發生時提供者可能不會呼叫 <xref:System.IObserver%601.OnError%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="19221-124">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="19221-125">例如，下列 `GetTemperature` 方法模擬此監視器每五秒鐘讀取一次溫度資料，並通知觀察者自上次讀取之後溫度是否已變更至少 1 度。</span><span class="sxs-lookup"><span data-stu-id="19221-125">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="19221-126">如果裝置未報告溫度 (即如果其值為 Null)，提供者會通知觀察者傳輸已完成。</span><span class="sxs-lookup"><span data-stu-id="19221-126">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="19221-127">請注意，除了呼叫每個觀察者的 <xref:System.IObserver%601.OnCompleted%2A> 方法，`GetTemperature` 方法可清除 <xref:System.Collections.Generic.List%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="19221-127">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="19221-128">在此情況下，提供者沒有呼叫其觀察者的 <xref:System.IObserver%601.OnError%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="19221-128">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="19221-129">範例</span><span class="sxs-lookup"><span data-stu-id="19221-129">Example</span></span>  
 <span data-ttu-id="19221-130">下列範例包含定義 <xref:System.IObservable%601> 溫度監視應用程式實作的完整原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="19221-130">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="19221-131">它包含 `Temperature` 結構，這是傳送給觀察者的資料，以及 `TemperatureMonitor` 類別，這是 <xref:System.IObservable%601> 實作。</span><span class="sxs-lookup"><span data-stu-id="19221-131">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="19221-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19221-132">See also</span></span>

- <xref:System.IObservable%601>
- [<span data-ttu-id="19221-133">觀察者設計模式</span><span class="sxs-lookup"><span data-stu-id="19221-133">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)
- [<span data-ttu-id="19221-134">如何：實作觀察者</span><span class="sxs-lookup"><span data-stu-id="19221-134">How to: Implement an Observer</span></span>](../../../docs/standard/events/how-to-implement-an-observer.md)
- [<span data-ttu-id="19221-135">觀察者設計模式最佳做法</span><span class="sxs-lookup"><span data-stu-id="19221-135">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
