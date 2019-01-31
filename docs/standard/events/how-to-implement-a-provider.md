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
# <a name="how-to-implement-a-provider"></a>HOW TO：實作提供者
觀察者設計模式需要提供者和一個或多個觀察者之間的分區，其中提供者會監視資料並傳送通知，而觀察者會接收來自提供者的通知 (回呼)。 本主題討論如何建立提供者。 相關主題為[如何：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)，討論如何建立觀察者。  
  
### <a name="to-create-a-provider"></a>建立提供者  
  
1.  定義提供者負責傳送給觀察者的資料。 雖然提供者和它傳送給觀察者的資料可以是單一的型別，但它們通常以不同型別代表。 例如，在溫度監控應用程式中，`Temperature` 結構定義的提供者 (在下一步中以 `TemperatureMonitor` 代表) 監視並由觀察者訂閱的資料。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  定義資料提供者，這是實作 <xref:System.IObservable%601?displayProperty=nameWithType> 介面的型別。 提供者的泛型型別引數是提供者傳送給觀察者的型別。 下列範例會定義 `TemperatureMonitor` 類別，這是包含泛型型別引數 `Temperature` 的建構 <xref:System.IObservable%601?displayProperty=nameWithType> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  決定提供者儲存對觀察者的參考之方式，讓每個觀察者在適當時被通知。 大多數情況下，如泛型 <xref:System.Collections.Generic.List%601> 物件等集合物件用於此用途。 下列範例定義在 `TemperatureMonitor` 中具現化的私用 <xref:System.Collections.Generic.List%601> 物件。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  定義提供者可傳回到訂閱者的 <xref:System.IDisposable> 實作，讓它們可隨時停止接收通知。 下列範例定義巢狀 `Unsubscriber` 類別，它在類別初始化時將參考傳遞到訂閱者集合及訂閱者。 此程式碼讓訂閱者能夠呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作，以將自己從訂閱者集合移除。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法。 該方法傳遞參考到 <xref:System.IObserver%601?displayProperty=nameWithType> 介面，並應該儲存在步驟 3 中為該目的而設計的物件中。 這個方法應再傳回在步驟 4 中開發的 <xref:System.IDisposable> 實作。 下列範例顯示 `TemperatureMonitor` 類別中 <xref:System.IObservable%601.Subscribe%2A> 方法的實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  藉由呼叫觀察者的 <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 實作，以適時通知它們。 在某些情況下，當錯誤發生時提供者可能不會呼叫 <xref:System.IObserver%601.OnError%2A> 方法。 例如，下列 `GetTemperature` 方法模擬此監視器每五秒鐘讀取一次溫度資料，並通知觀察者自上次讀取之後溫度是否已變更至少 1 度。 如果裝置未報告溫度 (即如果其值為 Null)，提供者會通知觀察者傳輸已完成。 請注意，除了呼叫每個觀察者的 <xref:System.IObserver%601.OnCompleted%2A> 方法，`GetTemperature` 方法可清除 <xref:System.Collections.Generic.List%601> 集合。 在此情況下，提供者沒有呼叫其觀察者的 <xref:System.IObserver%601.OnError%2A> 方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>範例  
 下列範例包含定義 <xref:System.IObservable%601> 溫度監視應用程式實作的完整原始程式碼。 它包含 `Temperature` 結構，這是傳送給觀察者的資料，以及 `TemperatureMonitor` 類別，這是 <xref:System.IObservable%601> 實作。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IObservable%601>
- [觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)
- [如何：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)
- [觀察者設計模式最佳做法](../../../docs/standard/events/observer-design-pattern-best-practices.md)
