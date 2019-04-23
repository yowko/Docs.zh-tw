---
title: HOW TO：實作觀察者
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b410b9381246cef2e61086e333c4c5b07646a575
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301057"
---
# <a name="how-to-implement-an-observer"></a>HOW TO：實作觀察者
觀察者設計模式需要觀察者和提供者之間的分區，其中觀察者會註冊通知，而提供者會監視資料並將通知傳送到一個或多個觀察者。 本主題討論如何建立觀察者。 相關主題為[如何：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)，討論如何建立提供者。  
  
### <a name="to-create-an-observer"></a>建立觀察者  
  
1. 定義觀察者，這是實作 <xref:System.IObserver%601?displayProperty=nameWithType> 介面的型別。 例如，下列程式碼定義名為 `TemperatureReporter` 的型別，它是包含 `Temperature` 泛型型別引數的建構 <xref:System.IObserver%601?displayProperty=nameWithType> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. 如果觀察者可以在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作之前停止接收通知，請定義會保留由提供者的 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法傳回之 <xref:System.IDisposable> 實作的私用變數。 您也應該定義訂閱方法，它會呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法並儲存傳回的 <xref:System.IDisposable> 物件。 例如，下列的程式碼定義名為 `unsubscriber` 的私用變數，並定義呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法之 `Subscribe` 方法，然後將傳回的物件指派到 `unsubscriber` 變數。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. 定義讓觀察者能夠在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作之前停止接收通知的方法 (如果需要此功能)。 下列範例定義 `Unsubscribe` 方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. 提供 <xref:System.IObserver%601> 介面定義的三個方法之實作：<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>，<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>。 視提供者和應用程式需求而定，<xref:System.IObserver%601.OnError%2A> 和 <xref:System.IObserver%601.OnCompleted%2A> 方法可以是虛設常式實作。 請注意，<xref:System.IObserver%601.OnError%2A> 方法不應將傳遞的 <xref:System.Exception> 物件當作例外狀況處理，而 <xref:System.IObserver%601.OnCompleted%2A> 方法可以自由呼叫提供者的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作。 下列範例顯示 `TemperatureReporter` 類別的 <xref:System.IObserver%601> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>範例  
 以下範例包含 `TemperatureReporter` 類別的完整原始程式碼，它提供溫度監視應用程式的 <xref:System.IObserver%601> 實作。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IObserver%601>
- [觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)
- [如何：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)
- [觀察者設計模式最佳做法](../../../docs/standard/events/observer-design-pattern-best-practices.md)
