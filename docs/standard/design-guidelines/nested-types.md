---
title: "巢狀類型 | Microsoft Docs"
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
  - "巢狀型別"
  - "公用巢狀型別"
  - "類型設計方針，巢狀型別"
  - "巢狀類型"
  - "輸入成員 [.NET Framework]"
  - "類別庫設計方針 [.NET Framework]，巢狀類型"
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 巢狀類型
巢狀型別是在另一個類型，稱為封入型別範圍內定義的類型。 巢狀型別具有與其封入型別的所有成員的存取權。 例如，具有存取權給私用欄位定義在封入型別，以及受保護的所有上階的封入型別中定義的欄位。  
  
 一般情況下，應該謹慎使用巢狀型別。 這有幾個原因。 有些開發人員不完全熟悉的概念。 這些開發人員，比方說，可能無法以巢狀型別變數的宣告語法。 巢狀型別也極為緊密結合其封入型別，並因此不適合一般用途的型別。  
  
 巢狀型別最適合用於模型化其封入類型的實作詳細資料。 使用者應該很少需要宣告巢狀型別的變數，而幾乎不應有明確具現化巢狀型別。 例如，集合的列舉值可以是該集合的巢狀型別。 列舉值通常是具現化依其封入類型，由於許多語言支援 foreach 陳述式，列舉值的變數很少需要使用者宣告。  
  
 **✓ 執行** 巢狀型別和其外部型別之間的關聯性時，成員存取範圍語意 （semantics） 是迫切需要使用巢狀型別。  
  
 **X 不** 使用公用巢狀型別做為邏輯群組建構，則使用這個命名空間。  
  
 **X 避免** 公開巢狀型別。 唯一的例外是巢狀型別的變數需要只在極少數的情況下，例如 subclassing 或其他進階的自訂案例中宣告。  
  
 **X 不** 使用巢狀型別，如果型別可能會參考外部包含型別。  
  
 例如，傳遞至方法，在類別定義列舉不應定義類別中的巢狀型別。  
  
 **X 不** 如果它們需要具現化用戶端程式碼使用巢狀型別。  如果型別具有公用建構函式，它應該可能不是巢狀。  
  
 如果型別可以具現化，這種機制來表示型別具有它自己的架構中的位置 （您可以建立、 使用它，並摧毀不需使用外部型別），並因此應該不巢狀。 內部型別應該不能廣泛地重複使用之外沒有任何關聯性的外部型別預設為外部型別。  
  
 **X 不** 定義巢狀型別為介面的成員。 許多語言不支援這類的建構。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)