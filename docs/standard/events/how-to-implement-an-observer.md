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
# <a name="how-to-implement-an-observer"></a>如何：實作觀察器
觀察器設計模式需要註冊通知時，觀察者和提供者，它可以監視資料和傳送通知給一個或多個觀察者之間的除法。 本主題討論如何建立觀察者。 相關的主題: < [How to： 實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)，討論如何建立提供者。  
  
### <a name="to-create-an-observer"></a>若要建立觀察者  
  
1.  定義觀察者，這是類型，可實作<xref:System.IObserver%601?displayProperty=nameWithType>介面。 例如，下列程式碼定義名為型別`TemperatureReporter`也就是建構<xref:System.IObserver%601?displayProperty=nameWithType>的泛型型別引數的實作`Temperature`。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  如果觀察者可以之前停止接收通知的提供者呼叫其<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作中，定義會保留私用變數<xref:System.IDisposable>實作提供者傳回<xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>方法。 您也應該定義呼叫的提供者的訂用帳戶方法<xref:System.IObservable%601.Subscribe%2A>方法，並傳回存放區<xref:System.IDisposable>物件。 例如，下列的程式碼會定義名為私用變數`unsubscriber`並定義`Subscribe`方法呼叫的提供者<xref:System.IObservable%601.Subscribe%2A>方法，並將傳回的物件指派`unsubscriber`變數。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  定義方法，讓觀察者來提供者呼叫之前停止接收通知及其<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>實作中，如果需要這項功能。 下列範例會定義`Unsubscribe`方法。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  提供所定義的三種方法的實作<xref:System.IObserver%601>介面： <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>， <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>，和<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>。 根據提供者和應用程式需求<xref:System.IObserver%601.OnError%2A>和<xref:System.IObserver%601.OnCompleted%2A>方法可以是虛設常式實作。 請注意，<xref:System.IObserver%601.OnError%2A>方法不應該處理傳入<xref:System.Exception>物件做為例外狀況，而<xref:System.IObserver%601.OnCompleted%2A>方法是呼叫提供者的免費<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作。 下列範例所示<xref:System.IObserver%601>實作`TemperatureReporter`類別。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>範例  
 下列範例包含的完整原始程式碼`TemperatureReporter`類別，可提供<xref:System.IObserver%601>溫度監控應用程式的實作。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IObserver%601>  
 [觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)  
 [操作說明：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [觀察者設計模式最佳做法](../../../docs/standard/events/observer-design-pattern-best-practices.md)
