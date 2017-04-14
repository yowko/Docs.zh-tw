---
title: "結構設計 | Microsoft Docs"
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
  - "類別庫設計方針 [.NET Framework] 結構"
  - "解除配置結構"
  - "配置結構"
  - "實值型別結構"
  - "結構設計"
  - "類型設計方針結構"
  - "結構 [.NET Framework] 設計指導方針"
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 結構設計
一般用途的實值型別通常稱為結構的 C\# 關鍵字。 本節提供一般結構設計指導方針。  
  
 **X 不** 結構提供預設建構函式。  
  
 遵循此指導方針，可讓結構，而不必在每個陣列項目上執行建構函式建立的陣列。 請注意，C\# 不允許有預設建構函式的結構。  
  
 **X 不** 定義可變動的實值型別。  
  
 可變動的實值型別有幾個問題。 例如，當屬性 getter 傳回實值型別時，呼叫端收到的複本。 以隱含方式建立的複製，因為開發人員可能不會察覺複製和原始值則不會變更。 此外，某些語言 （特別是，動態語言） 有問題使用可變動的實值型別，因為即使區域變數，取值時，會導致複本進行。  
  
 **✓ 執行** 確保所有執行個體資料的狀態設定為零，false 或 null （視需要） 無效。  
  
 這可以防止意外建立無效的執行個體時建立結構的陣列。  
  
 **✓ 執行** 實作 <xref:System.IEquatable%601> 實值型別上。  
  
 <xref:System.Object.Equals%2A?displayProperty=fullName> 實值型別上的方法會導致 boxing，和其預設實作不是非常有效率，因為它會使用反映。<xref:System.IEquatable%601.Equals%2A> 可能會更佳的效能，而且可以實作，這樣就不會造成 boxing。  
  
 **X 不** 明確地延長 <xref:System.ValueType>。 事實上，大部分語言防止這。  
  
 一般情況下，結構會非常有用，但僅用於小型、 單一、 不可變的值不會經常 boxed。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)