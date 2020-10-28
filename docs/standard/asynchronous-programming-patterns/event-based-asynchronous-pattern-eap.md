---
title: 事件架構非同步模式 (EAP)
description: 請參閱 .NET 中事件架構非同步模式 (EAP) 的相關文章連結，例如執行、最佳作法、實行 EAP 用戶端等。
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 16aabeb55a56c63449a865d00044c463657de740
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888837"
---
# <a name="event-based-asynchronous-pattern-eap"></a>事件架構非同步模式 (EAP)

將非同步功能公開到用戶端程式碼的方式有許多種； 事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。  
  
> [!NOTE]
> 從 .NET Framework 4 開始，工作平行程式庫會為非同步和平行程式設計提供新的模型。 如需詳細資訊，請參閱工作 [平行程式庫 (TPL) ](../parallel-programming/task-parallel-library-tpl.md) 和以工作 [為基礎的非同步模式 (請參閱) ](task-based-asynchronous-pattern-tap.md)。
  
## <a name="in-this-section"></a>本節內容

 [事件架構非同步模式概觀](event-based-asynchronous-pattern-overview.md)  
 描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。  
  
 [實作事件架構非同步模式](implementing-the-event-based-asynchronous-pattern.md)  
 描述將具有非同步功能的類別封裝起來的標準化方式。  
  
 [實作事件架構非同步模式的最佳作法](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 描述根據事件架構非同步模式來公開非同步功能的需求。  
  
 [決定何時實作事件架構非同步模式](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 描述如何判斷何時應選擇實作事件架構非同步模式，而非由[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md) 所代表的 <xref:System.IAsyncResult> 模式
  
 [作法：實作支援事件架構非同步模式的元件](component-that-supports-the-event-based-asynchronous-pattern.md)  
 描述如何建立實作事件架構非同步模式的元件。 其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。  

 [作法：實作事件架構非同步模式的用戶端](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 描述如何建立使用實作事件架構非同步模式之元件的用戶端。
  
 [作法：使用支援事件架構非同步模式的元件](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 描述如何使用可支援事件架構非同步模式的元件。  
  
## <a name="reference"></a>參考

 <xref:System.ComponentModel.AsyncOperation>  
 描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。  
  
## <a name="related-sections"></a>相關章節

 [工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 描述非同步處理和平行作業的程式設計模型。  
  
 [執行緒](../threading/index.md)  
 說明 .NET 中的多執行緒處理功能。  
  
## <a name="see-also"></a>請參閱

- [Managed 執行緒處理的最佳實施方針](../threading/managed-threading-best-practices.md)
- [事件](../events/index.md)
- [非同步程式設計模式](index.md)
