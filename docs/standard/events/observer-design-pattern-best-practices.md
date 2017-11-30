---
title: "觀察器設計模式最佳作法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0edba44efcaa46812f535b39364c2f5e4e3a1afe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="observer-design-pattern-best-practices"></a>觀察器設計模式最佳作法
在 .NET Framework 中，觀察者設計模式會實作為一組介面。 <xref:System.IObservable%601?displayProperty=nameWithType> 介面代表資料提供者，它也負責提供 <xref:System.IDisposable> 實作，讓觀察者可以取消訂閱通知。 <xref:System.IObserver%601?displayProperty=nameWithType> 介面代表觀察者。 本主題說明使用這些介面實作觀察者設計模式時，開發人員應該遵循的最佳作法。  
  
## <a name="threading"></a>執行緒處理  
 一般來說，提供者會藉由將特定觀察者加入由某些集合物件所代表的訂閱者清單，而實作 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法，且其會藉由從訂閱者清單中移除特定觀察者而實作 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法。 觀察者可隨時呼叫這些方法。 此外，因為提供者/觀察者合約未指定負責在 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 回呼方法之後取消訂閱的人員，所以提供者和觀察者可能會同時嘗試從清單中移除相同的成員。 因為這種可能性，<xref:System.IObservable%601.Subscribe%2A> 和 <xref:System.IDisposable.Dispose%2A> 方法都應該是安全執行緒。 一般而言，這涉及到使用[並行回收](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)或鎖定。 不是安全執行緒的實作，應該要明確地記載它們不是安全執行緒。  
  
 除了提供者/觀察者合約之外，還必須在某一層級指定所有其他保證。 當實作者強制要求其他需求時，應該清楚地宣布，以避免使用者對觀察者合約感到困惑。  
  
## <a name="handling-exceptions"></a>例外狀況處理  
 由於資料提供者和觀察者之間的鬆散連接，觀察者設計模式中的例外狀況傾向僅供參考。 這會影響提供者和觀察者處理觀察者設計模式中例外狀況的方式。  
  
### <a name="the-provider----calling-the-onerror-method"></a>提供者 -- 呼叫 OnError 方法  
 <xref:System.IObserver%601.OnError%2A> 方法旨在為觀察者提供參考訊息，和 <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> 方法很像。 不過，<xref:System.IObserver%601.OnNext%2A> 方法是設計來提供觀察者最近或更新過的資料，而 <xref:System.IObserver%601.OnError%2A> 方法則設計來指出提供者無法提供有效的資料。  
  
 提供者在處理例外狀況及呼叫 <xref:System.IObserver%601.OnError%2A> 方法時，應遵循這些最佳作法：  
  
-   如果有任何特定的需求，提供者必須處理它本身的例外狀況。  
  
-   提供者不應預期或要求觀察者以任何特定方式處理例外狀況。  
  
-   提供者應該在處理危害其提供更新能力的例外狀況時，呼叫 <xref:System.IObserver%601.OnError%2A> 方法。 這類例外狀況的詳細資訊，可以傳遞給觀察者。 在其他情況下，不需要通知觀察者有例外狀況。  
  
 一旦提供者呼叫了 <xref:System.IObserver%601.OnError%2A> 或<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 方法，便不應該再有進一步的通知，提供者可以取消訂閱其觀察者。 但觀察者也可以隨時取消訂閱自己，包括收到 <xref:System.IObserver%601.OnError%2A> 或 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 通知之前和之後。 觀察者設計模式不會指定提供者還是觀察者要否要負責取消訂閱；因此，有可能兩者都會嘗試取消訂閱。 一般而言，當觀察者取消訂閱時，它們會從訂閱者集合中移除。 在單一執行緒應用程式中，<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作應可確保物件參考有效，且物件是訂閱者集合的成員，然後再嘗試將它移除。 在多執行緒應用程式中，應使用安全執行緒的集合物件，例如 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 物件。  
  
### <a name="the-observer----implementing-the-onerror-method"></a>觀察者 -- 實作 OnError 方法  
 當觀察者收到來自提供者的錯誤通知時，觀察者應該將例外狀況視為參考，且應該不需要採取任何特定的動作。  
  
 在回應來自提供者的 <xref:System.IObserver%601.OnError%2A> 方法呼叫時，觀察者應該遵循這些最佳作法：  
  
-   觀察者不應該從其介面實作擲回例外狀況，例如 <xref:System.IObserver%601.OnNext%2A> 或 <xref:System.IObserver%601.OnError%2A>。 不過，如果觀察者沒有擲回例外狀況，它應該預期這些例外狀況不會受到處理。  
  
-   若要保留呼叫堆疊，則想要擲回傳遞給其 <xref:System.Exception> 方法之 <xref:System.IObserver%601.OnError%2A> 物件的觀察者，在擲回之前應該包裝該例外狀況。 對此用途應使用標準的例外狀況物件。  
  
## <a name="additional-best-practices"></a>其他最佳作法  
 嘗試在 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 方法中取消註冊，可能會導致 null 參考。 因此，我們建議您避免使用這種作法。  
  
 雖然您可以將觀察者附加到多個提供者，但建議的模式是將 <xref:System.IObserver%601> 執行個體只附加到一個 <xref:System.IObservable%601> 執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)  
 [操作說明：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [操作說明：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)
