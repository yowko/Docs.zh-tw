---
title: "類型設計方針 | Microsoft Docs"
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
  - "類型設計方針"
  - "類型設計方針，關於類型設計方針"
  - "類別庫設計方針 [.NET Framework] 類型設計方針"
  - "類型 [.NET Framework] 設計指導方針"
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 類型設計方針
從 CLR 觀點來看，有兩種類型的分類，參考類型和實值型別 — 但討論有關架構設計中，我們將為多個邏輯群組，各有其特定的設計規則類型。  
  
 類別是參考類型的一般情況。 它們會構成大量的大部分的架構中的型別。 類別欠其大受歡迎的豐富支援的物件導向的功能的設定以及其一般適用性。 基底類別和抽象類別會擴充性相關的特殊邏輯群組。  
  
 介面是由參考型別和實值型別能夠實作的型別。 他們因此可做為參考類型和實值型別多型階層的根項目。 此外，介面可以用來模擬原本並不支援 clr 中的多重繼承。  
  
 結構是實值類型的一般情況下，而且應該保留供小型的簡單類型，類似於語言基本類型。  
  
 列舉是特殊案例的實值型別用於定義短的值，例如週、 主控台色彩等等的天數。  
  
 靜態類別都是要做為靜態成員的容器的類型。 它們通常用於提供其他作業的捷徑。  
  
 委派、 例外狀況、 屬性、 陣列和集合的所有特殊的參考型別適用於特定用途，並為其設計和使用方式的指導方針將於他處討論這個活頁簿中。  
  
 **✓ 執行** 確保每種類型的一組定義明確之相關的成員，不只是隨機的不相關的功能集合。  
  
## 在本節中  
 [類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象類別設計](../../../docs/standard/design-guidelines/abstract-class.md)  
 [靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)  
 [介面設計](../../../docs/standard/design-guidelines/interface.md)  
 [結構設計](../../../docs/standard/design-guidelines/struct.md)  
 [列舉設計](../../../docs/standard/design-guidelines/enum.md)  
 [巢狀類型](../../../docs/standard/design-guidelines/nested-types.md)  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)