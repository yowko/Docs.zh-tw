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
# <a name="how-to-implement-a-provider"></a>如何：實作提供者
觀察器設計模式需要分區之間提供者，可監視資料並傳送通知時和一或多個的觀察者，從提供者會收到通知 （回呼）。 本主題討論如何建立提供者。 相關的主題: < [How to： 實作觀察器](../../../docs/standard/events/how-to-implement-an-observer.md)，討論如何建立觀察者。  
  
### <a name="to-create-a-provider"></a>若要建立提供者  
  
1.  定義提供者負責傳送給觀察者的資料。 雖然提供者，並針對它傳送給觀察者的資料可以是單一的類型，它們通常會以不同類型。 溫度監控應用程式，例如，在`Temperature`結構定義的資料，提供者 (這由`TemperatureMonitor`下一個步驟中定義的類別) 會監視並給哪些觀察者訂閱。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  定義資料提供者，這是類型，可實作<xref:System.IObservable%601?displayProperty=nameWithType>介面。 提供者的泛型型別引數是提供者會傳送給觀察者的類型。 下列範例會定義`TemperatureMonitor`類別，這是建構<xref:System.IObservable%601?displayProperty=nameWithType>的泛型型別引數的實作`Temperature`。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  判斷提供者會將儲存的方式給觀察者的參考，讓每個觀察者在適當時，會通知。 大多數情況下，例如泛型集合物件<xref:System.Collections.Generic.List%601>物件用於此用途。 下列範例會定義私人<xref:System.Collections.Generic.List%601>具現化中的物件`TemperatureMonitor`類別建構函式。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  定義<xref:System.IDisposable>provider 可以傳回給訂閱者，好讓它們可以停止接收通知，在任何時間的實作。 下列範例會定義巢狀`Unsubscriber`類別類別具現化時傳遞至訂閱者集合和訂閱者的參考。 此程式碼可讓呼叫物件的 「 訂閱者 」<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作其本身從 「 訂閱者 」 集合中移除。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法。 參考傳遞給方法<xref:System.IObserver%601?displayProperty=nameWithType>介面，並且應該儲存在針對此目的，在步驟 3 中設計的物件。 這個方法應再傳回<xref:System.IDisposable>開發步驟 4 中的實作。 下列範例顯示實作<xref:System.IObservable%601.Subscribe%2A>方法中的`TemperatureMonitor`類別。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  通知觀察者視需要透過呼叫其<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>， <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>，和<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作。 在某些情況下，提供者可能不會呼叫<xref:System.IObserver%601.OnError%2A>方法時發生錯誤。 例如，下列`GetTemperature`方法會模擬此監視會讀取溫度資料每隔五秒鐘，並通知觀察者溫度先前讀取之後，已變更至少.1 的角度。 如果裝置未報告的溫度 （也就是說，如果其值為 null），提供者會通知觀察者傳輸已完成。 請注意，除了呼叫每個觀察者<xref:System.IObserver%601.OnCompleted%2A>方法，`GetTemperature`方法清除<xref:System.Collections.Generic.List%601>集合。 在此情況下，提供者會沒有呼叫<xref:System.IObserver%601.OnError%2A>其觀察者的方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>範例  
 下列範例包含完整的原始程式碼定義<xref:System.IObservable%601>溫度監控應用程式的實作。 它包含`Temperature`結構，也就是傳送給觀察者的資料，而`TemperatureMonitor`類別，這是<xref:System.IObservable%601>實作。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IObservable%601>  
 [觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)  
 [操作說明：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [觀察者設計模式最佳做法](../../../docs/standard/events/observer-design-pattern-best-practices.md)
