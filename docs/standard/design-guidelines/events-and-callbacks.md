---
title: "事件和回呼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "事件 [.NET Framework] 擴充性"
  - "方法 [.NET Framework] 回呼"
  - "回呼方法"
  - "回呼"
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 事件和回呼
回呼是擴充功能，讓回呼至透過委派的使用者程式碼的架構。 這些委派通常會透過方法的參數傳遞給架構。  
  
 事件是一個特殊案例的回呼提供的委派 （事件處理常式） 的支援方便且一致的語法。 此外，Visual Studio 的陳述式完成和設計工具提供說明中使用以事件為基礎的 Api。 \(請參閱[事件設計](../../../docs/standard/design-guidelines/event.md)\)。  
  
 **✓ 考慮** 使用回呼，以允許使用者提供自訂程式碼執行的架構。  
  
 **✓ 考慮** 使用事件可讓使用者自訂的架構，而不需要了解物件導向設計的行為。  
  
 **✓ 執行** 偏好事件一般的回撥，因為它們是更廣泛的開發人員熟悉，而且會與 Visual Studio 陳述式完成整合。  
  
 **X 避免** 重視效能的 Api 中使用回呼。  
  
 **✓ 執行** 使用新 `Func<...>`, ，`Action<...>`, ，或 `Expression<...>` 類型而不是自訂委派，定義 Api 回呼時。  
  
 `Func<...>` 和 `Action<...>` 代表泛型委派。`Expression<...>` 代表函式定義可編譯及後續也地在執行階段，但可叫用序列化，並且傳遞至遠端處理程序。  
  
 **✓ 執行** 衡量並且了解使用的效能含意 `Expression<...>`, ，而不是使用 `Func<...>` 和 `Action<...>` 委派。  
  
 `Expression<...>` 型別是在大部分的情況下，邏輯上等同於 `Func<...>` 和 `Action<...>` 委派。 主要差異是委派會用來在本機處理序的情況下，這種狀況很有幫助和用於評估的運算式，在遠端處理序或電腦中可能是運算式。  
  
 **✓ 執行** 了解呼叫委派時，您會執行任意程式碼，並可能會有安全性、 正確性及相容性的影響。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)