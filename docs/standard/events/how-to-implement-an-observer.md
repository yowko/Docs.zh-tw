---
title: "如何：實作觀察器"
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="e5f01-102">如何：實作觀察器</span><span class="sxs-lookup"><span data-stu-id="e5f01-102">How to: Implement an Observer</span></span>
<span data-ttu-id="e5f01-103">觀察器設計模式需要註冊通知時，觀察者和提供者，它可以監視資料和傳送通知給一個或多個觀察者之間的除法。</span><span class="sxs-lookup"><span data-stu-id="e5f01-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="e5f01-104">本主題討論如何建立觀察者。</span><span class="sxs-lookup"><span data-stu-id="e5f01-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="e5f01-105">相關的主題: < [How to： 實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)，討論如何建立提供者。</span><span class="sxs-lookup"><span data-stu-id="e5f01-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="e5f01-106">若要建立觀察者</span><span class="sxs-lookup"><span data-stu-id="e5f01-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="e5f01-107">定義觀察者，這是類型，可實作<xref:System.IObserver%601?displayProperty=nameWithType>介面。</span><span class="sxs-lookup"><span data-stu-id="e5f01-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="e5f01-108">例如，下列程式碼定義名為型別`TemperatureReporter`也就是建構<xref:System.IObserver%601?displayProperty=nameWithType>的泛型型別引數的實作`Temperature`。</span><span class="sxs-lookup"><span data-stu-id="e5f01-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="e5f01-109">如果觀察者可以之前停止接收通知的提供者呼叫其<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作中，定義會保留私用變數<xref:System.IDisposable>實作提供者傳回<xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e5f01-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e5f01-110">您也應該定義呼叫的提供者的訂用帳戶方法<xref:System.IObservable%601.Subscribe%2A>方法，並傳回存放區<xref:System.IDisposable>物件。</span><span class="sxs-lookup"><span data-stu-id="e5f01-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="e5f01-111">例如，下列的程式碼會定義名為私用變數`unsubscriber`並定義`Subscribe`方法呼叫的提供者<xref:System.IObservable%601.Subscribe%2A>方法，並將傳回的物件指派`unsubscriber`變數。</span><span class="sxs-lookup"><span data-stu-id="e5f01-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="e5f01-112">定義方法，讓觀察者來提供者呼叫之前停止接收通知及其<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作中，如果需要這項功能。</span><span class="sxs-lookup"><span data-stu-id="e5f01-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="e5f01-113">下列範例會定義`Unsubscribe`方法。</span><span class="sxs-lookup"><span data-stu-id="e5f01-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="e5f01-114">提供所定義的三種方法的實作<xref:System.IObserver%601>介面： <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>， <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>，和<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e5f01-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e5f01-115">根據提供者和應用程式需求<xref:System.IObserver%601.OnError%2A>和<xref:System.IObserver%601.OnCompleted%2A>方法可以是虛設常式實作。</span><span class="sxs-lookup"><span data-stu-id="e5f01-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="e5f01-116">請注意，<xref:System.IObserver%601.OnError%2A>方法不應該處理傳入<xref:System.Exception>物件做為例外狀況，而<xref:System.IObserver%601.OnCompleted%2A>方法是呼叫提供者的免費<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作。</span><span class="sxs-lookup"><span data-stu-id="e5f01-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="e5f01-117">下列範例所示<xref:System.IObserver%601>實作`TemperatureReporter`類別。</span><span class="sxs-lookup"><span data-stu-id="e5f01-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="e5f01-118">範例</span><span class="sxs-lookup"><span data-stu-id="e5f01-118">Example</span></span>  
 <span data-ttu-id="e5f01-119">下列範例包含的完整原始程式碼`TemperatureReporter`類別，可提供<xref:System.IObserver%601>溫度監控應用程式的實作。</span><span class="sxs-lookup"><span data-stu-id="e5f01-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="e5f01-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5f01-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="e5f01-121">觀察者設計模式</span><span class="sxs-lookup"><span data-stu-id="e5f01-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="e5f01-122">操作說明：實作提供者</span><span class="sxs-lookup"><span data-stu-id="e5f01-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="e5f01-123">觀察者設計模式最佳做法</span><span class="sxs-lookup"><span data-stu-id="e5f01-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
