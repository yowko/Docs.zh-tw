---
title: "如何：實作提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "觀察器設計模式 [.NET Framework]，實作提供者"
  - "提供者 [.NET Framework]，觀察器設計模式"
  - "可預見值 [.NET Framework]，觀察器設計模式"
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：實作提供者
觀察者設計模式需要在監控資料和傳送通知的提供者，以及一個或多個接收提供者所送出通知 \(回呼\) 的觀察者之間加以劃分。  本主題討論如何建立提供者。  相關主題 [如何：實作觀察器](../../../docs/standard/events/how-to-implement-an-observer.md)將討論如何建立觀察者。  
  
### 若要建立提供者  
  
1.  定義提供者負責傳送給觀察者的資料。  雖然提供者和傳送給觀察者的資料可以是單一型別，但是兩者通常會以不同型別表示。  例如，在溫度監控應用程式中，`Temperature` 結構會定義提供者監控且觀察者訂閱的資料 \(以下一個步驟中所定義的 `TemperatureMonitor` 類別表示\)。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  定義資料提供者，其為實作 <xref:System.IObservable%601?displayProperty=fullName> 介面的型別。  提供者的泛型型別引數是提供者傳送給觀察者的型別。  下列範例會定義 `TemperatureMonitor` 類別，該類別為具有泛型型別引數 `Temperature` 的建構式 <xref:System.IObservable%601?displayProperty=fullName> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  判斷提供者如何儲存觀察者的參考，讓每個觀察者都能在適當時機收到通知。  最常用於此目的的是集合物件，像是泛型 <xref:System.Collections.Generic.List%601> 物件。  下列範例會定義私用 <xref:System.Collections.Generic.List%601> 物件，該物件會在 `TemperatureMonitor` 類別建構函式中執行個體化。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  定義提供者可以傳回給訂閱者的 <xref:System.IDisposable> 實作，如此訂閱者就可以隨時停止接收通知。  下列範例會定義巢狀 `Unsubscriber` 類別，在類別執行個體化時，會對該類別傳遞訂閱者集合參考和訂閱者參考。  此程式碼可讓訂閱者呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 實作，將其本身從訂閱者集合中移除。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> 方法。  此方法會接收傳遞的 <xref:System.IObserver%601?displayProperty=fullName> 介面參考，並且應該儲存在步驟 3 中專為該目的設計的物件中。  然後此方法就會傳回在步驟 4 中開發的 <xref:System.IDisposable> 實作。  下列範例會顯示 `TemperatureMonitor` 類別中 <xref:System.IObservable%601.Subscribe%2A> 方法的實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  藉由呼叫 <xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>、<xref:System.IObserver%601.OnError%2A?displayProperty=fullName> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> 實作的方式，適時通知觀察者。  在某些情況下，提供者可能不會在發生錯誤時呼叫 <xref:System.IObserver%601.OnError%2A> 方法。  例如，下列 `GetTemperature` 方法會模擬每五秒讀取溫度資料的監視器，並且在溫度與前一個讀數相差至少 .1 度時通知觀察者。  如果裝置未回報溫度 \(也就是其值為 null\)，提供者會通知觀察者傳輸已完成。  請注意，除了呼叫每個觀察者的 <xref:System.IObserver%601.OnCompleted%2A> 方法之外，`GetTemperature` 方法清除 <xref:System.Collections.Generic.List%601> 集合。  在此情況下，提供者不會呼叫其觀察者的 <xref:System.IObserver%601.OnError%2A> 方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## 範例  
 下列範例包含定義溫度監控應用程式之 <xref:System.IObservable%601> 實作的完整原始程式碼。  其中包括 `Temperature` 結構 \(也就是要傳送給觀察者的資料\) 以及 `TemperatureMonitor` 類別 \(也就是 <xref:System.IObservable%601> 實作\)。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## 請參閱  
 <xref:System.IObservable%601>   
 [觀察器設計模式](../../../docs/standard/events/observer-design-pattern.md)   
 [如何：實作觀察器](../../../docs/standard/events/how-to-implement-an-observer.md)   
 [觀察器設計模式最佳作法](../../../docs/standard/events/observer-design-pattern-best-practices.md)