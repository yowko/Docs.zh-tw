---
title: "如何：實作觀察器 | Microsoft Docs"
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
  - "觀察器 [.NET Framework]，觀察器設計模式"
  - "觀察器設計模式 [.NET Framework]，實作觀察器"
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：實作觀察器
觀察者設計模式需要在註冊通知的觀察者，以及監控資料和傳送通知給一個或多個觀察者的提供者之間加以劃分。  本主題將討論如何建立觀察者。  相關主題 [如何：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)將討論如何建立提供者。  
  
### 若要建立觀察者  
  
1.  定義觀察者，其為實作 <xref:System.IObserver%601?displayProperty=fullName> 介面的型別。  例如，下列程式碼會定義名為 `TemperatureReporter` 的型別，該型別為具有泛型型別引數 `Temperature` 的建構式 <xref:System.IObserver%601?displayProperty=fullName> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  如果觀察者可以在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> 實作之前停止接收通知，請定義用來保存提供者的 <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> 方法所傳回 <xref:System.IDisposable> 實作的私用變數。  您也應該定義呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法並且儲存所傳回 <xref:System.IDisposable> 物件的訂閱方法。  例如，下列程式碼會定義名為 `unsubscriber` 的私用變數，並且定義呼叫提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法以及將傳回的物件指派給 `unsubscriber` 變數的 `Subscribe` 方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  定義一個方法，讓觀察者在提供者呼叫其 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> 實作之前停止接收通知 \(如果此功能未必要\)。  下列範例會定義 `Unsubscribe` 方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  提供 <xref:System.IObserver%601> 介面所定義三種方法的實作：<xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>、<xref:System.IObserver%601.OnError%2A?displayProperty=fullName> 和 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>。  根據提供者和應用程式的需要而定，<xref:System.IObserver%601.OnError%2A> 和 <xref:System.IObserver%601.OnCompleted%2A> 方法可以是 Stub 實作。  請注意，<xref:System.IObserver%601.OnError%2A> 方法不應該將傳遞的 <xref:System.Exception> 物件當做例外狀況處理，而且 <xref:System.IObserver%601.OnCompleted%2A> 方法可自由呼叫提供者的 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 實作。  下列範例示範 `TemperatureReporter` 類別的 <xref:System.IObserver%601> 實作。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## 範例  
 下列範例包含 `TemperatureReporter` 類別的完整原始程式碼，該類別會提供溫度監控應用程式的 <xref:System.IObserver%601> 實作。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## 請參閱  
 <xref:System.IObserver%601>   
 [觀察器設計模式](../../../docs/standard/events/observer-design-pattern.md)   
 [如何：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)   
 [觀察器設計模式最佳作法](../../../docs/standard/events/observer-design-pattern-best-practices.md)