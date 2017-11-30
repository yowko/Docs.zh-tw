---
title: "如何：實作提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="4d057-102">如何：實作提供者</span><span class="sxs-lookup"><span data-stu-id="4d057-102">How to: Implement a Provider</span></span>
<span data-ttu-id="4d057-103">觀察器設計模式需要分區之間提供者，可監視資料並傳送通知時和一或多個的觀察者，從提供者會收到通知 （回呼）。</span><span class="sxs-lookup"><span data-stu-id="4d057-103">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="4d057-104">本主題討論如何建立提供者。</span><span class="sxs-lookup"><span data-stu-id="4d057-104">This topic discusses how to create a provider.</span></span> <span data-ttu-id="4d057-105">相關的主題: < [How to： 實作觀察器](../../../docs/standard/events/how-to-implement-an-observer.md)，討論如何建立觀察者。</span><span class="sxs-lookup"><span data-stu-id="4d057-105">A related topic, [How to: Implement an Observer](../../../docs/standard/events/how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="4d057-106">若要建立提供者</span><span class="sxs-lookup"><span data-stu-id="4d057-106">To create a provider</span></span>  
  
1.  <span data-ttu-id="4d057-107">定義提供者負責傳送給觀察者的資料。</span><span class="sxs-lookup"><span data-stu-id="4d057-107">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="4d057-108">雖然提供者，並針對它傳送給觀察者的資料可以是單一的類型，它們通常會以不同類型。</span><span class="sxs-lookup"><span data-stu-id="4d057-108">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="4d057-109">溫度監控應用程式，例如，在`Temperature`結構定義的資料，提供者 (這由`TemperatureMonitor`下一個步驟中定義的類別) 會監視並給哪些觀察者訂閱。</span><span class="sxs-lookup"><span data-stu-id="4d057-109">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  <span data-ttu-id="4d057-110">定義資料提供者，這是類型，可實作<xref:System.IObservable%601?displayProperty=nameWithType>介面。</span><span class="sxs-lookup"><span data-stu-id="4d057-110">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="4d057-111">提供者的泛型型別引數是提供者會傳送給觀察者的類型。</span><span class="sxs-lookup"><span data-stu-id="4d057-111">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="4d057-112">下列範例會定義`TemperatureMonitor`類別，這是建構<xref:System.IObservable%601?displayProperty=nameWithType>的泛型型別引數的實作`Temperature`。</span><span class="sxs-lookup"><span data-stu-id="4d057-112">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  <span data-ttu-id="4d057-113">判斷提供者會將儲存的方式給觀察者的參考，讓每個觀察者在適當時，會通知。</span><span class="sxs-lookup"><span data-stu-id="4d057-113">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="4d057-114">大多數情況下，例如泛型集合物件<xref:System.Collections.Generic.List%601>物件用於此用途。</span><span class="sxs-lookup"><span data-stu-id="4d057-114">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="4d057-115">下列範例會定義私人<xref:System.Collections.Generic.List%601>具現化中的物件`TemperatureMonitor`類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="4d057-115">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  <span data-ttu-id="4d057-116">定義<xref:System.IDisposable>provider 可以傳回給訂閱者，好讓它們可以停止接收通知，在任何時間的實作。</span><span class="sxs-lookup"><span data-stu-id="4d057-116">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="4d057-117">下列範例會定義巢狀`Unsubscriber`類別類別具現化時傳遞至訂閱者集合和訂閱者的參考。</span><span class="sxs-lookup"><span data-stu-id="4d057-117">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="4d057-118">此程式碼可讓呼叫物件的 「 訂閱者 」<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作其本身從 「 訂閱者 」 集合中移除。</span><span class="sxs-lookup"><span data-stu-id="4d057-118">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <span data-ttu-id="4d057-119">實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4d057-119">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4d057-120">參考傳遞給方法<xref:System.IObserver%601?displayProperty=nameWithType>介面，並且應該儲存在針對此目的，在步驟 3 中設計的物件。</span><span class="sxs-lookup"><span data-stu-id="4d057-120">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="4d057-121">這個方法應再傳回<xref:System.IDisposable>開發步驟 4 中的實作。</span><span class="sxs-lookup"><span data-stu-id="4d057-121">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="4d057-122">下列範例顯示實作<xref:System.IObservable%601.Subscribe%2A>方法中的`TemperatureMonitor`類別。</span><span class="sxs-lookup"><span data-stu-id="4d057-122">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  <span data-ttu-id="4d057-123">通知觀察者視需要透過呼叫其<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>， <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>，和<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作。</span><span class="sxs-lookup"><span data-stu-id="4d057-123">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="4d057-124">在某些情況下，提供者可能不會呼叫<xref:System.IObserver%601.OnError%2A>方法時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d057-124">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="4d057-125">例如，下列`GetTemperature`方法會模擬此監視會讀取溫度資料每隔五秒鐘，並通知觀察者溫度先前讀取之後，已變更至少.1 的角度。</span><span class="sxs-lookup"><span data-stu-id="4d057-125">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="4d057-126">如果裝置未報告的溫度 （也就是說，如果其值為 null），提供者會通知觀察者傳輸已完成。</span><span class="sxs-lookup"><span data-stu-id="4d057-126">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="4d057-127">請注意，除了呼叫每個觀察者<xref:System.IObserver%601.OnCompleted%2A>方法，`GetTemperature`方法清除<xref:System.Collections.Generic.List%601>集合。</span><span class="sxs-lookup"><span data-stu-id="4d057-127">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="4d057-128">在此情況下，提供者會沒有呼叫<xref:System.IObserver%601.OnError%2A>其觀察者的方法。</span><span class="sxs-lookup"><span data-stu-id="4d057-128">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="4d057-129">範例</span><span class="sxs-lookup"><span data-stu-id="4d057-129">Example</span></span>  
 <span data-ttu-id="4d057-130">下列範例包含完整的原始程式碼定義<xref:System.IObservable%601>溫度監控應用程式的實作。</span><span class="sxs-lookup"><span data-stu-id="4d057-130">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="4d057-131">它包含`Temperature`結構，也就是傳送給觀察者的資料，而`TemperatureMonitor`類別，這是<xref:System.IObservable%601>實作。</span><span class="sxs-lookup"><span data-stu-id="4d057-131">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="4d057-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d057-132">See Also</span></span>  
 <xref:System.IObservable%601>  
 [<span data-ttu-id="4d057-133">觀察者設計模式</span><span class="sxs-lookup"><span data-stu-id="4d057-133">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="4d057-134">操作說明：實作觀察者</span><span class="sxs-lookup"><span data-stu-id="4d057-134">How to: Implement an Observer</span></span>](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [<span data-ttu-id="4d057-135">觀察者設計模式最佳做法</span><span class="sxs-lookup"><span data-stu-id="4d057-135">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
