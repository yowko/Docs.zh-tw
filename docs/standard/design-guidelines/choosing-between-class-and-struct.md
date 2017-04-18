---
title: "類別和結構之間選擇 | Microsoft Docs"
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
  - "類別庫設計方針 [.NET Framework] 類別"
  - "類別與結構 [.NET Framework]"
  - "類別 [.NET Framework] 設計指導方針"
  - "類型設計方針結構"
  - "結構 [.NET Framework] 設計指導方針"
  - "結構與類別 [.NET Framework]"
  - "類型設計方針類別"
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 類別和結構之間選擇
每個架構設計工具所面臨的基本設計決策的其中一個是設計為 （參考型別） 的類別或結構 （數值型別） 的型別。 深入了解的參考類型和實值型別行為差異是非常重要的選擇。  
  
 參考類型和實值型別，我們會考慮的第一個差異是，參考類型的配置在堆積和記憶體回收，而實值型別會配置堆疊或內嵌於包含類型和取消配置在堆疊回溯時，或當其包含的型別取得解除配置。 因此，配置和取消配置的實值型別是一般比參考類型的配置和解除便宜。  
  
 接下來，參考類型的陣列配置外行，這表示的陣列項目是只是在堆積上的參考型別的執行個體的參考。 值型別陣列的配置是內嵌，也就是說，陣列元素實值型別的實際的執行個體。 因此，值型別陣列的配置和解除是參考型別陣列的配置和解除比成本更低。 此外，在大部分情況下的值型別陣列，會表現出多參考位置較佳。  
  
 下一項差異被與記憶體使用量。 取得 boxed 實值型別，當轉型為參考型別或其中一個所實作的介面。 他們會取得 unboxed 時轉型為實值型別。 因為方塊是配置在堆積和記憶體回收、 過度 boxing 和 unboxing 是物件可以有堆積、 記憶體回收行程，以及最終的應用程式效能的負面影響。  相反地，參考型別會轉換會不發生任何這類 boxing。  
  
 接下來，參考的型別指派會複製參考，而值的型別指派複製整個值。 因此，大型的參考類型的指派較低的大型值型別指派比。  
  
 最後，參考型別是傳址方式傳遞，而傳值方式傳遞實值型別。 參考類型的執行個體的變更會影響所有指向執行個體的參考。 依值傳遞時，會複製值型別執行個體。 變更的實值型別執行個體時，它當然不會影響任何其複本。 因為複本不由使用者明確建立，但會以隱含方式建立引數會傳遞或傳回值傳回時，您可以變更的實值型別可能會混淆多個使用者。 因此，實值型別應該是不變。  
  
 根據經驗法則，大部分的架構中的型別必須是類別。 有，不過，某些情況下，在其中特性實值型別讓它更適合使用結構。  
  
 **✓ 考慮** 定義結構，而不是類別，如果型別的執行個體很小，且通常短期或嵌入其他物件。  
  
 **X 避免** 定義結構，除非該型別具有下列特性的所有︰  
  
-   它以邏輯方式表示的單一值，類似於基本型別 \(`int`, ，`double`, 等等。\)。  
  
-   它具有執行個體大小小於 16 個位元組。  
  
-   它是不變。  
  
-   它不會經常 boxed。  
  
 在其他情況下，您應該做為類別定義您的型別。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)