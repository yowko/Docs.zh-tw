---
title: 使用事件架構非同步模式設計多執行緒程式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
ms.openlocfilehash: 26e555a158ced352c297952b56f7557cbd825cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a>使用事件架構非同步模式設計多執行緒程式
將非同步功能公開到用戶端程式碼的方式有許多種； 事件架構非同步模式會針對要呈現非同步行為之類別指示建議的方法。  
  
## <a name="in-this-section"></a>本節內容  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。  
  
 [實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 描述將具有非同步功能的類別封裝起來的標準化方式。  
  
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 描述根據事件架構非同步模式來公開非同步功能的需求。  
  
 [決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 描述如何判斷何時應該選擇實作事件架構非同步模式，而不是 <xref:System.IAsyncResult> 模式。  
  
 [逐步解說：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 說明如何建立實作事件架構非同步模式的元件。 其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。  
  
 [操作說明：使用支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 描述如何使用可支援事件架構非同步模式的元件。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.AsyncOperation>  
 描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。  
  
## <a name="see-also"></a>請參閱  
 [Managed 執行緒處理的最佳實施方針](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [事件](../../../docs/standard/events/index.md)  
 [元件中的多執行緒](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
